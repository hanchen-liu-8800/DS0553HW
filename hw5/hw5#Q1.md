#Q1.
#distinct directors
MATCH (p:Person)-[d:PRODUCED]->(m:Movie)
RETURN distinct p

#distinct actors
MATCH (p:Person)-[d:ACTED_IN]->(m:Movie)
RETURN distinct p