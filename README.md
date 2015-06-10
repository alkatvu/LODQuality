# LODQuality
Benchmark For The Quality of FactForge's Answers

Over the past decade, the Semantic Web community has built and adopted a set 
f synthetic benchmarks to test storage, inference and query functionality. 
Some of the most well-known benchmarks such as the LUBM, [10], the extended 
eLUBM benchmark [11] and the Berlin SPARQL benchmark [2] are all examples of 
these. However, all these are synthetic datasets. There is a shortage of 
realistic benchmarks that provide realistic queries plus validated (“Gold 
Standard”) answers. As a first contribution of this paper, we remedy this 
situation by producing a new benchmark that consists of a set of 50 general 
knowledge questions, a set of Gold Standard (GS) answers for each of these 
questions, and a faithful (expert validated) SPARQL translation of each of 
these questions. The entire resource (original questions, their SPARQL 
translations, the Gold Standard answers, as well as query-results against 
FactForge) are available online at 
http://www.larkc.eu/resources/published-data-sources, and we consider this 
to be a contribution of this work. This section describes the details of 
our benchmark. 

For an experiment investigating how people search for information in their 
memory, [15] designed a set of general knowledge questions. Each question 
identifies a natural category by a domain label (e.g.,‘Geography’) and a 
verbal description (e.g., ‘Name African countries’) and asks participants 
to enumerate as many exemplars as possible (e.g., ‘Algeria’, ‘Angola’, ‘
Benin’, etc.). Questions were drawn from diverse areas of general knowledge 
(e.g., arts, brands, sciences, sports) and included “Name members of the pop 
band ABBA”, “Name Nobel laureates in literature since 1945”, etc. [15] 
determined a set of correct answers for each question. The number of true 
exemplars varied widely between categories (from 4 to 200 items). Particular 
care was given to the completeness of the answer set by including alternative 
labels (e.g., ‘Democratic Republic of the Congo’, ‘Zaire’) and spelling 
variants (‘Kongo’).

We have developed a set of 50 SPARQL queries, made to resemble the questions 
from [15]. For this translation, we used a number of well-known namespaces, 
such as DBPedia, Freebase, Geonames, Umbel, etc. Any such translation is 
difficult, error-prone, and raises the question how faithful the SPARQL 
queries are to the original natural-language questions. To analyse this, the 
creator of the original questions (one of the authors of [15]) verified the 
veracity of the SPARQL queries. Thirty-eight (76%) of the SPARQL queries were 
deemed “identical” to the original question, and the remaining 24% were described 
as “close”. Consequently, we trust that the correspondence between the questions 
and corresponding SPARQL queries is high and sufficient for our purposes. 
In particular, the Gold Standard answers for the set of natural language questions 
can also be used as a Gold Standard for the set of SPARQL queries.

The benchmark’s 50 queries were randomly distributed over time dependent (24 
queries) and time independent (26 queries) categories. In this paper, we define a 
query with answers that varies through time as time dependent questions. An example 
of a time dependent question will be “Name Wimbledon winners for women’s or men’s 
singles (since 1980).” Among the 26 time independent queries, six queries aimed to 
assess the revenue of some generic companies such as coffee companies, oil companies, 
beer companies, technology companies, fashion and exiting brands (see Table 1). With 
respect to these six specific questions, on the one hand the task proved to be difficult 
to provide a complete set of Gold Standard answers given the time and resources at hand. 
On the other hand, none of the LOD’s available resources attached year metadata to a 
given companies’ revenue, making it impossible to generate a correct time independent 
query. As the digital representation of the real world companies on the LOD was therefore 
incomplete, the respective generated SPAQL query did not provide any answers when the 
queries were made more specific by adding a year constraint. Given that these six queries 
could not be used at this point in time, our analysis focused mainly only on the remaining 
44 queries.

Table 1 List of intractable questions.
Questions intractable over FactForge
45 Name Coffee brands with a value exceeding $600 million (in 2009)
46 Name oil companies with a value exceeding $700 million (in 2009)
47 Name existing fashion brands worth over $1 billion (in 2009)
48 Name beer brands with over $1 billion in sales (in 2008)
49 Name technology brands with a value exceeding $5 billion (in 2009)
50 Name existing brands worth over $20 billion (in 2009)

To complete this benchmark collection, we executed all of our queries against FactForge. 
Although FactForge is a subset of the entire Web of Data, it is currently one of the largest 
available subsets that is both closed under inference and queryable. The remaining 44 SPARQL 
queries could be answered by FactForge and their quality could be measured using the 44 
respective Gold Standard answers sets which all together represent a set of 1455 Gold Standard 
answers. To complete this benchmark collection, we executed all of our queries against FactForge. 
Although FactForge is a subset of the entire Web of Data, it is currently one of the largest 
available subsets that is both closed under inference and queryable. On June 1, 2015, our 44 
queries produced 1080 distinct answers (i.e., 1080 distinct URIs). Four answers were duplicated 
answers even though they were presented with distinct resources. Those answers were removed from 
the collection bringing the total numbers of answers under investigation to 1076. URIs came with 
natural-language labels (specified through an rdfs:label, skos:prefLabel, dbp-prop:capital, or 
fb:type.object.name property), in English. In this paper, the usage of rdfs:label refers to the 
list of all natural-language labels listed above. To this end, all labels candidate were scored by 
a human judge on a 5-point Likert scale, indicating their perceived correctness. During this extensive 
scoring, the human judge used background knowledge sources (online pages and encyclopedia) and was 
asked to proceed at reasonable speed. Since the semantics of OWL and RDF assumes that URIs are 
meaningless identifiers (e.g. opencyc:Mx4rwUIMiJwpEbGdrcN5Y29ycA, denoting the oil company BP), 
the rankings of the human judge were based on the natural language label properties listed earlier 
for each of the answers. All answer URIs contained multiple natural-language labels, and we calculated 
the ranking of a URI as the maximum of the ranks assigned to its associated rdfs:label. This is reasonable 
because unfamiliar labels received low scores from the human judge even if there was another label for 
the same URI that was recognized as a correct answer.


