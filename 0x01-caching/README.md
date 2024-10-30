# Caching System

This project implements different caching systems using Python. Each cache class inherits from a base class, `BaseCaching`, which defines the main structure and configuration of the caching system.

## BaseCaching Class

The `BaseCaching` class sets up the caching system and contains:
- **MAX_ITEMS**: The maximum number of items allowed in the cache, set to 4.
- **Methods**:
  - `put(key, item)`: Adds an item to the cache.
  - `get(key)`: Retrieves an item from the cache.

The caching classes defined below inherit from `BaseCaching` and implement different caching policies.

---

## Task 1: BasicCache
A simple caching system without a limit on the number of items.

- **Features**:
  - Stores items in `self.cache_data`.
  - No eviction; all items remain in the cache indefinitely.
- **Methods**:
  - `put(key, item)`: Adds an item to the cache if `key` and `item` are not `None`.
  - `get(key)`: Returns the item linked to `key` or `None` if `key` is invalid.

---

## Task 2: FIFOCache
A caching system implementing a **First In, First Out (FIFO)** eviction policy.

- **Features**:
  - Stores items in `self.cache_data`.
  - Evicts the oldest item if the cache exceeds `MAX_ITEMS`.
- **Methods**:
  - `put(key, item)`: Adds an item and discards the oldest item if the cache exceeds `MAX_ITEMS`.
  - `get(key)`: Retrieves the item linked to `key` or `None` if `key` is invalid.

---

## Task 3: LIFOCache
A caching system implementing a **Last In, First Out (LIFO)** eviction policy.

- **Features**:
  - Stores items in `self.cache_data`.
  - Evicts the most recently added item if the cache exceeds `MAX_ITEMS`.
- **Methods**:
  - `put(key, item)`: Adds an item and discards the most recent item if the cache exceeds `MAX_ITEMS`.
  - `get(key)`: Retrieves the item linked to `key` or `None` if `key` is invalid.

---

## Task 4: LRUCache
A caching system implementing a **Least Recently Used (LRU)** eviction policy.

- **Features**:
  - Stores items in `self.cache_data` using `OrderedDict` to maintain item order.
  - Evicts the least recently accessed item if the cache exceeds `MAX_ITEMS`.
- **Methods**:
  - `put(key, item)`: Adds an item and discards the least recently used item if the cache exceeds `MAX_ITEMS`.
  - `get(key)`: Retrieves the item linked to `key`, updating it to the most recently used.

---

## Task 5: MRUCache
A caching system implementing a **Most Recently Used (MRU)** eviction policy.

- **Features**:
  - Stores items in `self.cache_data`.
  - Evicts the most recently accessed item if the cache exceeds `MAX_ITEMS`.
- **Methods**:
  - `put(key, item)`: Adds an item and discards the most recently used item if the cache exceeds `MAX_ITEMS`.
  - `get(key)`: Retrieves the item linked to `key`, updating it as the most recently used.

---

## Task 6: LFUCache
A caching system implementing a **Least Frequently Used (LFU)** eviction policy, with **Least Recently Used (LRU)** as a tie-breaker.

- **Features**:
  - Stores items in `self.cache_data` and tracks frequency in `self.usage_count`.
  - Evicts the least frequently used item, or the least recently used among items with the same frequency, if the cache exceeds `MAX_ITEMS`.
- **Methods**:
  - `put(key, item)`: Adds an item and discards the least frequently used item if the cache exceeds `MAX_ITEMS`.
  - `get(key)`: Retrieves the item linked to `key`, updating its frequency count.

---

Each class implements a unique caching policy to manage data efficiently. This structure allows comparison between different eviction strategies and explores how various caching techniques impact performance.

---

## Usage Example

To use any of the cache classes, create an instance of the desired class and use `put()` and `get()` methods to interact with the cache.

```python
from cache_class_name import ClassName

cache = ClassName()
cache.put("key1", "value1")
cache.get("key1")

