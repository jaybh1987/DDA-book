# Data Models and Query Languages
The Limits of my language mean the limits of my world.

Data Models is most important part of making software. Most applications are built by layering one data model on top of another. 

key question is: how is it represented in terms of the next-lower layer? e.g

You make objects of entities from real world. 
You express them in terms of json,xml,tables in rdb or graph model.
Engineers build db software decided on a way of representing that json/xml/relational/graph data in terms of bytes in memory,on disk, or on network. The representation may allow data to be quried, searched,manipulated & process in various ways. 
Yet lower levels, Engineers have figured out how to represent bytes in terms of electrical currents, pulses or light, magnetic fields and more. 

idea is simple each layer hide the complexity of layer below it by providing clean data model.

Choose data model is very important, decides what your application will able to do, it is important to choose appropriate data model.

We will compare **relational model**,**document model** and **graph-based** data models.


### Relational Model Versus Document Model

**Relational DB**:  
- Relational model dominated for 25 to 30 years. 
- The roots of relational databases lie in business data processing, which was performed
  on mainframe computers in the 1960s and ’70s.
-  The use cases appear mundane from
   today’s perspective: typically transaction processing (entering sales or banking trans‐
   actions, airline reservations, stock-keeping in warehouses) and batch processing (cus‐
   tomer invoicing, payroll, reporting).