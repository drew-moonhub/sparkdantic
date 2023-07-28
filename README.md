##  sparkdantic

> 1️⃣ version: 0.1.0

> ✍️ author: Mitchell Lisle

# PySpark Model Conversion Tool

This Python module provides a utility for converting Pydantic models to PySpark schemas. It's implemented as a class named `SparkModel` that extends the Pydantic's `BaseModel`.

## Features

- Conversion from Pydantic model to PySpark schema.
- Determination of nullable types.
- Customizable type mapping between Python and PySpark data types.

## Dependencies

This module depends on the following libraries:
- `pydantic`
- `pyspark`
- Python's built-in `datetime`, `decimal`, `types`, and `typing` modules

## Usage

### Creating a new SparkModel

A `SparkModel` is a Pydantic model, and you can define one by simply inheriting from `SparkModel` and defining some fields:

```python
class MyModel(SparkModel):
    name: str
    age: int
    hobbies: List[str]
```

### Generating a PySpark Schema

You can generate a PySpark schema from the model fields using the `spark_schema()` method:

```python
my_model = MyModel()
spark_schema = my_model.spark_schema()
```

Provides this schema:

```python
StructType([
    StructField('name', StringType(), True),
    StructField('age', IntegerType(), True),
    StructField('hobbies', ArrayType(StringType(), False), True)
])
```
