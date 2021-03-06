---

title: Inferring the gender of a face in an image
abstract: The subject matter of this specification can be embodied in, among other things, a computer-implemented method that includes receiving a plurality of images having human faces. The method further includes generating a data structure having representations of the faces and associations that link the representations based on similarities in appearance between the faces. The method further includes outputting a first gender value for a first representation of a first face that indicates a gender of the first face based on one or more other gender values of one or more other representations of one or more other faces that are linked to the first representation.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08041082&OS=08041082&RS=08041082
owner: Google Inc.
number: 08041082
owner_city: Mountain View
owner_country: US
publication_date: 20071102
---
In many application domains such as photo collection social networking surveillance adult content detection etc it is desirable to use an automated method to determine the gender of a person in an image. Some systems use computer vision algorithms in an attempt to determine gender by directly analyzing a face within an image to determine if the face is associated with typically male or female characteristics.

In general this document describes inferring the gender of a person or animal from a set of images. The faces are represented in a data structure and includes links between faces having similarities.

In a first aspect a computer implemented method includes receiving a plurality of images having human faces. The method further includes generating a data structure having representations of the faces and associations that link the representations based on similarities in appearance between the faces. The method further includes outputting a first gender value for a first representation of a first face that indicates a gender of the first face based on one or more other gender values of one or more other representations of one or more other faces that are linked to the first representation.

In a second aspect a computer implemented method includes receiving a plurality of images having animal faces. The method further includes generating a graph having nodes representing the faces and edges that link the nodes based on similarities in appearance between the faces represented by the nodes. The method further includes outputting a first gender value for a first node that indicates a gender of a first face associated with the first node based on one or more second gender values of one or more neighboring nodes in the graph.

In a third aspect a computer implemented method includes receiving a plurality of images having animal faces. The method further includes generating a data structure that associates a first face with one or more second faces based on similarities in appearance between the first face and the one or more second faces. The method further includes outputting a first gender value for the first face based on one or more gender values previously associated with the one or more second faces.

In a fourth aspect a system includes a face detector for identifying faces within images. The system further includes means for generating a data structure configured to associate a first face with one or more second faces based on similarities in appearance between the first face and the one or more second faces. The system further includes an interface to output a first gender value for the first face based on one or more gender values previously associated with the one or more second faces.

The systems and techniques described here may provide one or more of the following advantages. First an automated method is provided for identifying the gender of a person or persons in a collection of images. Second a gender detection method is provided that does not require large data sets for training a statistical gender classifier. Third a method for gender detection is provided that does not rely on computer vision techniques to directly identify a gender of a face based on an image of the face. Fourth genders associated with androgynous faces within images can be more accurately determined.

The details of one or more embodiments are set forth in the accompanying drawings and the description below. Other features and advantages will be apparent from the description and drawings and from the claims.

This document describes systems and techniques for inferring the gender of a face in an image. A network such as the Internet or a wide area network can include servers hosting images of people and or other animals. In general an image of a female face may have similarities with images of other female faces and an image of a male face may have similarities with images of other male faces. In certain implementations a gender determination system analyzes the similarities between the faces including faces having a known gender and faces having an unknown gender. The gender determination system can use the similarities and the known genders to infer a gender of one or more faces having an unknown gender.

In certain implementations a face having an unknown gender may have little or no direct similarities with the faces having a known gender. The gender determination system may determine that the face having the unknown gender has similarities with one or more other unknown gender faces. The gender determination system may also determine that one or more of the other unknown gender faces have similarities with one or more faces having known genders. The gender determination system can use the chain of intermediate faces to infer the gender of the face having an unknown gender by indirectly relating the unknown gender face to a face having a known gender.

In the case of HTTP communication the publisher systems can include multiple web pages respectively. For example the web page published by the blogging system is a celebrity gossip blog the web page published by the image hosting system is an image gallery and the web page published by the web server system is a homepage for the ACME Corporation. The web pages each include one or more images . The images include faces of people and or other animals. The gender determination system retrieves the images from the publisher systems and stores the images in a data storage .

The gender determination system includes an inferred gender label generator that performs processing to infer the gender of the faces in the images. The inferred gender label generator includes a face detector and a similarity calculator . The face detector uses face detection algorithms known to those skilled in the art to detect faces in the images . In certain implementations the face detector stores the portions of the images that include faces in the data storage . Alternatively the face detector may store information that describes the location of the face portions within the images . The face detector passes the face information to the similarity calculator or otherwise notifies the similarity calculator of the face information.

The similarity calculator calculates similarity scores between pairs of faces. The similarity calculator uses facial analysis algorithms known to those skilled in the art. For example one such facial analysis algorithm is discussed in a paper entitled Transformation Ranking and Clustering for Face Recognition Algorithm Comparison by Stefan Leigh Jonathan Phillips Patrick Grother Alan Heckert Andrew Ruhkin Elaine Newton Mariama Moody Kimball Kniskern Susan Heath published in association with the Third Workshop on Automatic Identification Advanced Technologies Tarrytown March 2002.

The inferred gender label generator includes or has access to predetermined gender information for one or more of the faces. For example a user may make an input indicating that a face in the image has a gender of female and a face in the image has a gender of male. Alternatively the inferred gender label generator may generate predetermined gender information based on an algorithm such as associating a distinguishing feature within a face as male or female. The inferred gender label generator uses the predetermined gender information and the similarity scores between the faces to link each of the faces directly or indirectly to the faces having predetermined or known genders. The inferred gender label generator uses the links to infer a gender for the faces. The inferred gender label generator stores the similarity scores and inferred genders in the data storage as a gender label value table .

The gender determination system can output genders of the faces as gender label information for the images respectively to the publisher systems . In another implementation the gender determination system can include or provide gender information to an image search engine. For example a user may make an input indicating a search for images of people or animals having a particular gender. The gender determination system or another image search system uses the gender label information to provide images having the requested gender.

In the system the similarity calculator is included in a graph generator . The graph generator generates a graph of the faces in the images . Each face represents a node in the graph. The graph generator represents the similarity scores between faces as edges that link the nodes. Each edge is associated with its similarity score. The edges linking the nodes may be undirected bi directional or uni directional. For the purposes of clarity the edges in the following examples are undirected unless otherwise specified.

The inferred gender label generator associates each face with one or more gender labels and each gender label may have a gender label value. In some implementations the gender label values are numeric values such as decimal numbers. For example the face in the image may have gender labels of Male and Female with associated gender label values of 0.00 and 1.00 respectively. The inferred gender label generator stores the gender label values in the gender label value table .

In some implementations the gender determination system includes a data storage that stores one or more predetermined gender label values . The gender determination system may receive the predetermined gender label values for example from a user input. The graph generator associates the predetermined gender label values with corresponding nodes in the graph. For example a user may input the gender label values of 0.00 Male and 1.00 Female for the face in the image . The graph generator associates the gender label values with the node in the graph that represents the face from the image . The inferred gender label generator subsequently uses the predetermined gender label values as a starting point or seed for the algorithm to infer other gender label values of faces included in other images.

For example the similarity calculator may determine similarity scores of 0.7 between the faces and 0.5 between the faces and and 0.7 between the faces and . The similarity scores of 0.7 indicate that the faces and are significantly similar and the faces and are significantly similar. The similarity score of 0.5 indicates that the faces and are only somewhat similar.

The similarity calculator may perform the comparison and calculate a similarity score for each pair of images. The graph generator uses the similarity scores to generate the graph representing similarities between the faces 

In this example of a weighted undirected graph each node eventually has a Male gender label and a Female gender label e.g. either predetermined or inferred . The nodes have predetermined Male and Female gender labels and label values. As described below the inferred gender label generator uses the weighted undirected graph to infer Male and Female gender label values for the nodes . Although this example describes two gender labels in other implementations a node may have zero three or more gender labels as well.

In some implementations the inferred gender label generator also infers gender label values for nodes having predetermined gender label values. Inferred gender label values for nodes having predetermined gender label values can be used to check the accuracy of the inferred gender label generator and or to check for possible errors in the predetermined gender label values .

The method can start with step which identifies face regions using a face detector. For example the inferred gender label generator can use the face detector to locate the regions of the images and that include the faces and respectively.

In step the method compares two faces and generates a similarity score representing the similarity between the two faces. For example the similarity calculator compares the faces and and calculates the similarity score of 0.7 between the faces and

If at step there are more faces to compare then the method returns to step and compares another pair of faces. Otherwise the method constructs a weighted undirected graph at step where the faces are nodes and the similarity scores are edges that link the nodes. For example the graph generator constructs the nodes and representing the faces and . The graph generator links the nodes and with an edge associated with the similarity score of 0.7 between the nodes and

At step the method receives a user input labeling a subset of the face nodes as either male or female. For example the gender determination system may receive a user input including the predetermined gender label values . The predetermined gender label values indicate that the node has gender label values of 1.0 Male and 0.0 Female. The inferred gender label generator uses the weighted undirected graph and the predetermined gender label values to infer the gender of one or more faces represented by nodes in the weighted undirected graph .

The adsorption algorithm can be executed using information from the graphs shown in and can be executed for every node in the graphs. The adsorption algorithm can start with step which determines if a specified number of iterations have run for a graph. If the number is not complete step is performed. In step a node representing a face is selected. For example the inferred gender label generator can select a node that has gender label values that may be modified by the algorithm such as Male or Female. 

In step a gender label is selected from the selected node. For example the inferred gender label generator can select the gender label Male if present in the selected node. In step a gender label value for the selected gender label is initialized to zero. For example the inferred gender label generator can set the gender label value for Male to zero.

In step a neighboring node of the selected node can be selected. For example the selected node may specify that a neighboring node has a similarity score of 0.7 with the selected node. The inferred gender label generator can select the neighboring node.

In step a corresponding weighted gender label value of a selected neighbor is added to a gender label value of the selected gender label. For example if the selected neighboring node has a gender label value for the gender label Male the inferred gender label generator can add this value to the selected node s gender label value for Male. In certain implementations the gender label value retrieved from a neighboring node can be weighted to affect the contribution of the gender label value based on the degree of distance from the selected node e.g. based on whether the neighboring node is linked directly to the selected node linked by two edges to the selected node etc. In some implementations the gender label value can also be based on a weight or similarity score associated with the edge.

In step it is determined whether there is another neighbor node to select. For example the inferred gender label generator can determine if the selected node is linked by a single edge to any additional neighbors that have not been selected. In another example a user may specify how many degrees out e.g. linked by two edges three edges etc. the inferred gender label generator should search for neighbors. If there is another neighbor that has not been selected steps and can be repeated as indicated by step . If there is not another neighbor step can be performed.

In step it is determined whether there is another gender label in the selected node. For example the selected node can have multiple gender labels such as Male and Female. If these additional gender labels have not been selected the inferred gender label generator can select one of the previously unselected gender labels and repeat steps . If all the gender labels in the node have been selected the gender label values of the selected node can be normalized as shown in step . For example the inferred gender label generator can normalize each gender label value so that it has a value between 0 and 1 where the gender label value s magnitude is proportional to its contribution relative to all the gender label values associated with that node.

In step it can be determined whether there are additional nodes in the graph to select. If there are additional nodes the method can return to step . If all the nodes in the graph have been selected the method can return to step to determine whether the specified number of iterations has been performed on the graph. If so the adsorption algorithm can end.

In certain implementations after x iterations the inferred gender label generator can examine one or more of the nodes of the graph and probabilistically assign a gender label to each node based on the weights of the gender labels e.g. a label with the maximum label value can be assigned to the node .

In some implementations the number of the iterations is specified in advance. In other implementations the algorithm terminates when the gender label values for the gender labels at each node reach a steady state e.g. a state where the difference in the label value change between iterations is smaller than a specified epsilon .

In another alternative method gender label values for nodes can be inferred by executing a random walk algorithm on the graphs. More specifically in some implementations given a graph G the inferred gender label generator can calculate gender label values or label weights for every node by starting a random walk from each node. The random walk algorithm can include reversing the direction of each edge in the graph if the edge is directed. If the edge is bi directional or undirected the edge can be left unchanged.

The inferred gender label generator can select a node of interest and start a random walk from that node to linked nodes. At each node where there are multiple out nodes e.g. nodes with links to multiple other nodes the inferred gender label generator can randomly select an edge to follow. If the edges are weighted the inferred gender label generator can select an edge based on the edge s weight e.g. the greatest weighted edge can be selected first .

If during the random walk a node is selected that is a labeling node e.g. used as a label for other nodes the classification for this walk is the label associated with the labeling node. The inferred gender label generator can maintain a tally of the labels associated with each classification.

If during the random walk a node is selected that is not a labeling node the inferred gender label generator selects the next random path or edge to follow.

The inferred gender label generator can repeat the random walk multiple times e.g. 1000s to 100 000s of times for each node of interest. After completion the inferred gender label generator can derive the gender label values based on the tally of labels. This process can be repeated for each node of interest.

Additionally in some implementations the inferred gender label generator generates a second data structure such as a second graph. The second graph can include nodes substantially similar to the weighted undirected graph . In one example the weighted undirected graph includes Male gender label values and a second graph includes Female gender label values.

In some implementations the adsorption algorithm can also be performed on the second graph. The inferred gender label generator can select and compare the resulting label value magnitudes for a corresponding node from both the first and second graphs. In some implementations the inferred gender label generator can combine the gender label value magnitudes from each graph through linear weighting to determine a final gender label value magnitude e.g. the first graph s gender label value contributes 0.7 and the second graph s gender label value contributes 0.3 . In other implementations the gender label values can be weighed equally to determine the final gender label value e.g. 0.5 0.5 or the inferred gender label generator can give one gender label value its full contribution while ignoring the gender label value from the other graph e.g. 1.0 0.0 or 0.0 1.0 .

In other implementations the inferred gender label generator can use a cross validation method to set the contribution weights for gender label value magnitudes from each graph. For example the inferred gender label generator can access nodes in a graph where the nodes have gender label value magnitudes that are known. The inferred gender label generator can compare the actual gender label value magnitudes with the known gender label value magnitudes. The inferred gender label generator can then weight each graph based on how closely its gender label values match the known gender label values.

In certain implementations the inferred gender label generator can compare the gender label value magnitudes to an expected a priori distribution instead of or in addition to examining the final gender label magnitudes. For example if a summed value of a first gender label across all nodes is 8.0 and the summed value of a second gender label across all of the nodes is 4.0 the a priori distribution suggests that first gender label may be twice as likely to occur as the second gender label. The inferred gender label generator can use this expectation to calibrate the gender label value magnitudes for each node. If in a particular node the first gender label value is 1.5 and the second gender label value is 1.0 then the evidence for the first gender label although higher than the second gender label is not as high as expected because the ratio is not as high as the a priori distribution. This decreases the confidence that the difference in magnitudes is meaningful. A confidence factor can be translated back into the rankings.

In some implementations if the difference in magnitudes is below a confidence threshold the inferred gender label generator can rank a gender label with a lower value above a gender label with a higher value e.g. manipulate the lower value so that it is increased to a gender label value greater than the higher value . For example if the first gender label s value is expected to be three times the value of the second gender label but was only 1.1 times greater than the second gender label the inferred gender label generator can rank the second gender label above the first gender label. In some implementations the confidence factor can be kept as a confidence measure which can be used for example by machine learning algorithms to weight the resultant label value magnitudes.

In yet other implementations instead of or in addition to comparing the gender label value magnitudes based on the a priori distribution of the nodes the inferred gender label generator can compare the gender label value magnitudes based on an end distribution of magnitudes across all nodes. For example the inferred gender label generator can measure how different a particular node s distribution is from an average calculated across all nodes in a graph.

The weighted undirected graph includes predetermined gender label values for the nodes of 0.00 Male and 1.00 Male respectively. The nodes have initial gender label values of 0.50 Male. In some implementations an initial gender label value may be a predetermined value such as 0.50. Alternatively the initial gender label value may be based on the average of the predetermined gender label values or another set of gender label values.

Referring to the weighted undirected graph now shows the Male gender label values of the nodes after one iteration of the inferred gender label generator . In this example the Male gender label values of the nodes are fixed at 0.00 and 1.00 respectively. The Male gender label values of the nodes are now 0.25 0.73 and 0.53 respectively. The relatively high similarity between the nodes and as compared to other nodes gives the node a Male gender label value 0.25 close to the Male gender label value of the node 0.00 . Similarly the relatively high similarity between the nodes and as compared to other nodes gives the node a Male gender label value 0.73 close to the Male gender label value of the node 1.00 . The node has slightly higher similarity with the nodes and leading to a Male gender value 0.53 that leans toward Male.

Referring to the weighted undirected graph now shows the gender label values for the nodes after two iterations of the inferred gender label generator . The Male gender label value of the node has increased by 0.01 to 0.26. The Male gender label value of the node has increased by 0.01 to 0.74. The Male gender label value of the node has increased by 0.01 to 0.54. In some implementations the inferred gender label generator may stop processing a graph after the change in each gender label value is below a particular threshold such as 0.01. 

Referring to the weighted undirected graph now shows the gender label values for the nodes after four iterations of the inferred gender label generator . The Male gender label value of the node has increased by 0.01 to 0.75. The Male gender label values of the nodes have now converged within 0.01. The inferred gender label generator stops processing the weighted undirected graph and outputs the Male gender label values. Alternatively the inferred gender label generator may stop processing after a predetermined number of iterations such as five iterations.

In some implementations the inferred gender label generator infers Female gender label values for the nodes in addition to the Male gender label values previously described. The inferred gender label generator can compare and or combine the Male and Female gender label values to determine a gender for the faces associated with the nodes . For example if the Male gender label value of a node is larger than its Female gender label value than the corresponding face is determined to be Male and vice versa for Female.

In certain implementations dummy labels can be used in all of the graphs generated by the inferred label generator. In other implementations a user may specify for which graph s the dummy labels may be used.

The example of dummy labels shown here associates a dummy node with each of the nodes in the weighted undirected graph . In other implementations dummy labels are assigned to a small number of nodes such as nodes that are not associated with initial gender label values.

The memory stores information within the generic computing system . In one implementation the memory is a computer readable medium. In one implementation the memory is a volatile memory unit. In another implementation the memory is a non volatile memory unit.

The storage device is capable of providing mass storage for the generic computing system . In one implementation the storage device is a computer readable medium. In various different implementations the storage device may be a floppy disk device a hard disk device an optical disk device or a tape device.

The input output device provides input output operations for the generic computing system . In one implementation the input output device includes a keyboard and or pointing device. In another implementation the input output device includes a display unit for displaying graphical user interfaces.

The features described can be implemented in digital electronic circuitry or in computer hardware firmware software or in combinations of them. The apparatus can be implemented in a computer program product tangibly embodied in an information carrier e.g. in a machine readable storage device or in a propagated signal for execution by a programmable processor and method steps can be performed by a programmable processor executing a program of instructions to perform functions of the described implementations by operating on input data and generating output. The described features can be implemented advantageously in one or more computer programs that are executable on a programmable system including at least one programmable processor coupled to receive data and instructions from and to transmit data and instructions to a data storage system at least one input device and at least one output device. A computer program is a set of instructions that can be used directly or indirectly in a computer to perform a certain activity or bring about a certain result. A computer program can be written in any form of programming language including compiled or interpreted languages and it can be deployed in any form including as a stand alone program or as a module component subroutine or other unit suitable for use in a computing environment.

Suitable processors for the execution of a program of instructions include by way of example both general and special purpose microprocessors and the sole processor or one of multiple processors of any kind of computer. Generally a processor will receive instructions and data from a read only memory or a random access memory or both. The essential elements of a computer are a processor for executing instructions and one or more memories for storing instructions and data. Generally a computer will also include or be operatively coupled to communicate with one or more mass storage devices for storing data files such devices include magnetic disks such as internal hard disks and removable disks magneto optical disks and optical disks. Storage devices suitable for tangibly embodying computer program instructions and data include all forms of non volatile memory including by way of example semiconductor memory devices such as EPROM EEPROM and flash memory devices magnetic disks such as internal hard disks and removable disks magneto optical disks and CD ROM and DVD ROM disks. The processor and the memory can be supplemented by or incorporated in ASICs application specific integrated circuits .

To provide for interaction with a user the features can be implemented on a computer having a display device such as a CRT cathode ray tube or LCD liquid crystal display monitor for displaying information to the user and a keyboard and a pointing device such as a mouse or a trackball by which the user can provide input to the computer.

The features can be implemented in a computer system that includes a back end component such as a data server or that includes a middleware component such as an application server or an Internet server or that includes a front end component such as a client computer having a graphical user interface or an Internet browser or any combination of them. The components of the system can be connected by any form or medium of digital data communication such as a communication network. Examples of communication networks include e.g. a LAN a WAN and the computers and networks forming the Internet.

The computer system can include clients and servers. A client and server are generally remote from each other and typically interact through a network such as the described one. The relationship of client and server arises by virtue of computer programs running on the respective computers and having a client server relationship to each other

Although a few implementations have been described in detail above other modifications are possible. For example image or facial labels other than gender may be used such as ethnicity or complexion.

In addition the logic flows depicted in the figures do not require the particular order shown or sequential order to achieve desirable results. In addition other steps may be provided or steps may be eliminated from the described flows and other components may be added to or removed from the described systems. Accordingly other implementations are within the scope of the following claims.

