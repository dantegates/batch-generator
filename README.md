# batch-generator
A generic class for generating batches of training data.

# Examples
Below are some examples of extending the class `data.BaseBatchGenerator`.

```python
class FileBatchGenerator(BaseBatchGenerator):
    def generate_batches(self, steps, batch_size, n_batches):
        for i in range(n_batches):
            X = np.array(steps[i*batch_size:(i+1)*(batch_size)])
            yield self.pad_batch(X)
        
    def generate_steps(self, item):
        steps = []
        with open(item) as f:
            for L in f:
                steps.append(self.process_line(L))
        return steps
                
    def process_line(self, line):
        """Convert line to numpy array"""
        ...
        
    def pad_batch(self, X):
        ...
```
