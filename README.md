# cyclus-example-transactions

This repo includes an example of Cyclus. It contains four files

* the .xml file is the Cyclus input file. It was taken, unmodified, from example input files for the Cyclus facility modules called [Cycamore](https://github.com/cyclus/cycamore)
* the .sqlite file is the Cyclus output file. It contains raw data about the facilities deployed, resources traded, transaction records, and the supply and demand for various commodities.
* a data.csv file, which converts information from the transaction records into a csv format that has a single line per transaction. The columns should be relatively self-explanatory, and the last few columns track isotopics in [PyNE nucname](http://pyne.io/theorymanual/nucname.html) format, ZZAAASSSS
* a data-cleaned.csv file, which does two things to build on the first csv file.
  * if there are any time steps with multiple transactions of an identical commodity between the same two facilities (i.e. a mine sends two shipments of 1 kg ore to the mill at timestep 4), then the transactions are consolidated (i.e. to a single, 2 kg transaction of ore from the mine to the mill at timestep 4)
  * zero-transactions are recorded between every set of facilities who trade at least once during the simulation. For example, if the mine sends the mill 1 kg on odd timesteps, then a fake 0 kg transaction is recorded on even timesteps
