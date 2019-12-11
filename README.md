# Diebold-Mariano test for predictive accuracy

The DM test compares the forecast accuracy of different forecasting methods. This implementation (Python function *dm_test* in *stat_test*) is designed according to R implementation which could be found here: https://pkg.robjhyndman.com/forecast/reference/dm.test.html

## Installation

```
python setup.py install
```

## Usage

### Input
- **e1**: forecast errors from the first method
- **e2**: forecast errors from the second method
- **alternative**: str specifying the alternative hypothesis, 'two_sided' (default one), 'less' or 'greater'
- **h**: forcasting horizon used in calculating errors (e1, e2), default value is 1
- **power**: power used in the loss function (usually 1 or 2), default value is 2
    
## Return 
Named tuple containing DM statistic and p-value:
- **dm_stat**: DM statistics
- **p_value**: p-value of DM statistic

### Example

```python
import numpy as np
from stat_test import dm_test

np.random.seed(42)
e1 = np.random.rand(100)
e2 = np.random.rand(100)
dm_test(e1, e2, h=1, power=2, alternative='two_sided')
# dm_test_result(dm_stat=-0.5522212106658311, p_value=0.5820413576449055)
```