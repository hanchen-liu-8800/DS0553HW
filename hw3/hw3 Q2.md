# a.
db.grades.distinct('class_id').length

# b.
db.grades.distinct('student_id').length

# c.
db.grades.aggregate([
  {
    $unwind: "$scores"
  },
  {
    $match: { 
        'scores.type': 'exam', 
        class_id: 212 
    }
  },
  {
    $group: {
      _id: {
        class_id: '$class_id',
        score_type: '$scores.type'
      },
      "avgScore": { $avg: '$scores.score' }
    }
  }
])

# d.
db.grades.aggregate([
  {
    $unwind: "$scores"
  },
  {
    $match: { 
        'scores.type': 'exam', 
        class_id: 212 
    }
  },
  {
    $group: {
      _id: {
        class_id: '$class_id',
        score_type: '$scores.type'
      },
      "stdScore": { $stdDevSamp: '$scores.score' }
    }
  }
])