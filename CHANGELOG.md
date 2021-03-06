## 1.2.0 - 2020-08-17

### Added

<u>GradientBoostedTreesModeler</u>

- modeler.build_model() and modeler.train() now parallelize training over time horizons

<u>PanelDataProcessor</u>

- processor.build_processed_data() and processor.process_all_columns() now parallelize processing over columns

<u>Command-line Interface</u>

- Command-line execution now produces calibration and forecast error outputs

<u>Utils</u>

- Option within create_example_data() to specify number of persons and time periods in dataset

### Fixed

- Null category added to columns of pandas Categorical type in PanelDataProcessor
- Command-line execution now trains modeler for specific number of test intervals if specified

## 1.1.0 - 2020-07-20

### Added

<u>GradientBoostedTreesModeler and FeedforwardNeuralNetworkModeler</u>

- Support for hyperoptimization with modeler.hyperoptimize()
- Options within modeler.build_model() and modeler.train() for:
  - hyperparameters (such as those returned by hyperoptimization)
  - toggling off validation early stopping (using params argument in the case of build_model())
  - training on subset
- Defaults for all configuration parameters
- Default option to represent datetime features represented YYYYMMDD integers
- Option to represent datetime features as nanoseconds

<u>PanelDataProcessor</u>

- "\_period" and "\_maximum_lead" columns, which replace computation of "factorized time ids" in various methods
- Defaults for all configuration parameters
- Categorical feature conversion to pandas Categorical type

<u>Command-line Interface</u>

- Option to execute from command line without configuration file
- Option to specify individual parameter values
- Default configuration for processors and modelers
- Command-line execution now uses data file in current directory if there is only one file with a matching extension

### Removed

<u>PanelDataProcessor</u>

- Numeric feature normalization
- Homebrewed categorical feature integer mapping
- Raw subsetting

<u>Command-line Interface</u>

- Interacted fixed effects modeling
- Metrics-related output when no test set specified
- Forecast-related output when test set specified

### Fixed

- Validation and test sets no longer overlap
- modeler.evaluate() now reports correct metrics for subsets in which maximum observable period varies (e.g., train and test set combined)
- First period of test set now considered observed for computing training set outcomes
- ProportionalHazards models can now be saved to files
- Code now formatted using _Black_
- Command-line interface now evaluates on earliest period of test set instead of validation set

