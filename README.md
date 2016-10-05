# <img src="https://github.com/anfederico/Waldo/blob/master/Waldo.png" height=30px width=30px>&nbsp;Waldo
<i>Software designed to identify and monitor social/historical cues for short term stock movement</i>

### Python Requirements
    csv
    os
    selenium
    numpy
    matplotlib
    sklearn

### Raw Data Requirements    
    CSV containing raw historical data for each stock
    
    TSLA_RawData.csv
    Date,Open,High,Low,Close,Volume
    09/02/2015,245.3,247.88,239.78,247.69,4629174
    09/03/2015,252.06,252.08,245,245.57,4194772
    09/04/2015,240.89,244.09,238.2,241.93,3689153
    
### MakeTrainingData.py
    This program will read in Raw Data and write out Training Data
    Infile Path = path/to/RawData
    Outfile Path = path/to/TrainingData
    Training Data can then be fed directly to the classification algorithm
    
### Radial Basis Function Support Vector Machine (RBFSVM.py)
    This program reads in Training Data and feeds it to the classification algorithm via sci-kit learn
    Please visit: http://scikit-learn.org/stable/auto_examples/svm/plot_rbf_parameters.html before adjusting parameters
    Part of the training data is reserved for accuracy testing (this parameter can be changed)
    Note that accuracy may not be indicative of good/bad clustering in terms of finding hot spots
    Left: Training (Dark) and Testing (Light) Data
    Right: Training and Testing Data with gradient clustering
    Blue = Positive (+) / Red = Negative (-)

<p align="center">
<img src="https://github.com/anfederico/Waldo/blob/master/TSLA_Plot.png"/>
</p>

### Monitor Stocks for Favorable Conditions (DataCrawler.py)
    DataCrawler.py is a headless web browser using selenium
    This tool can be used to access daily stock indicators after the model is trained with historical data
    
    Upon execution, the program will:
        1. Travel to Fidelity
        2. Access their research tools for a particular stock
        3. Automatically fill credentials (requires a Fidelity account)
        4. Access advanced charting mode
        5. Select indicators of choice
        6. Download a spreadsheet of the data
    
    This data can then be automatically plugged into the model and predict whether the conditions are favorable to make a trade  
    Note: To edit this program, considering using Firebug/Firepath to identify your XPaths of interest
    
