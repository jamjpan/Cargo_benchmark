This repository contains benchmark problem instances and road networks
for the [Cargo](https://github.com/jamjpan/Cargo) ridesharing simulator.

Problem `*.instance` format:

```
    Line 1: (instance name)
    Line 2: (road network) TAXI
    Line 3: VEHICLES (number of vehicles)
    Line 4: CUSTOMERS (number of customers)
    Line 5: (blank line)
    Line 6: (header row)
    Line 7-end: vehicles and customers
```

The columns for lines 7 and beyond are described by the header in line 6. Some
notes about the columns:

- ORIGIN and DEST identify nodes found in the `*.rnet` file indicated by Line 2.
- A negative Q indicates a vehicle, and |Q| gives the vehicle's capacity.
- A DEST of -1 indicates a "taxi", in other words a vehicle without its own destination.
- A LATE of -1 indicates a vehicle never ends its service.

Road network `*.edges` format:

```
    Line 1: (number nodes) (number edges)
    Line 2-end: (node_1) (node_2) (weight)
```

Road network `*.rnet` format:

```
    Col 1: (edge id)      , a 0-indexed ID for the edge
    Col 2: (node_1)       , the ID of node_1 from edges file
    Col 3: (node_2)       , the ID of node_2 from edges file
    Col 4: (lng)          , longitude of node_1
    Col 5: (lat)          , latitude of node_1
    Col 6: (lng)          , longitude of node_2
    Col 7: (lat)          , latitude of node_2
```

Each (Col 2, Col 3) pair in the `*.rnet` file matches a line in the corresponding
`*.edges` file. To visualize an `*.rnet` file, use the gnuplot command

```plot 'bj5.rnet' u 4:5:($6-$4):($7-$5) w vectors nohead```

