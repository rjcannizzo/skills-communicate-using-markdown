### Strategy Pattern
This is the classsic OOP implementation (See 'Dive into Design Patterns' PDF)
Often implemented with functions rather than classes in Python

#### Components
1. Context
2. Client
3. Strategy Interface

```python
from abc import ABC, abstractmethod

class StrategyInterface(ABC):
    @abstractmethod
    def execute(self):
        pass

class StrategyOne(StrategyInterface):
    def execute(self):
        pass

class StrategyTwo(StrategyInterface):
    def execute(self):
        pass

class Context:
    def __init__(self, strategy: StrategyInterface = None) -> None:
        self.strategy = strategy
    
    def set_strategy(self, new_strategy: StrategyInterface):
        """Replace existing strategy, if any, with a new one."""
        self.strategy = new_strategy

    def do_work(self):
        self.strategy.execute()

class Client:
    def main(self):
        strategy = StrategyOne()
        context = Context(strategy=strategy)
        context.do_work()
        context.set_strategy(StrategyTwo())
        context.do_work()
```
