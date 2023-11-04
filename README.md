# AirBnB Clone - The Console

Welcome to the AirBnB Clone project's command-line interface (CLI), the first segment of the AirBnB project at Holberton School. This CLI is designed to manage objects for the AirBnB (HBnB) website, providing a foundation for the development of a complete AirBnB website. The goal of this project is to eventually deploy a server that mimics the functionality of the AirBnB website.

## Functionalities of the Command Interpreter

The command interpreter offers the following functionalities:

1. Create a new object (e.g., User or Place).
2. Retrieve an object from a file or a database.
3. Perform operations on objects (count, compute stats, etc.).
4. Update attributes of an object.
5. Destroy an object.

## Table of Contents

- [Environment](#environment)
- [Installation](#installation)
- [File Descriptions](#file-descriptions)
- [Usage](#usage)
- [Examples of Use](#examples-of-use)
- [Bugs](#bugs)
- [Authors](#authors)
- [License](#license)

## Environment

This project is interpreted and tested on Ubuntu 14.04 LTS using Python 3 (version 3.4.3).

## Installation

1. Clone this repository:
   ```shell
   git clone https://github.com/alexaorrico/AirBnB_clone.git
   ```

2. Access the AirBnB directory:
   ```shell
   cd AirBnB_clone
   ```

3. Run the CLI interactively:
   ```shell
   ./console
   ```

4. Or run the CLI non-interactively by piping a command:
   ```shell
   echo "<command>" | ./console.py
   ```

## File Descriptions

### `console.py`

The `console.py` file contains the entry point of the command interpreter and supports the following commands:

- `EOF` - exits the console
- `quit` - exits the console
- `<emptyline>` - overwrites the default empty line method and does nothing
- `create` - Creates a new instance of `BaseModel`, saves it (to the JSON file), and prints the ID.
- `destroy` - Deletes an instance based on the class name and ID (saves the change into the JSON file).
- `show` - Prints the string representation of an instance based on the class name and ID.
- `all` - Prints all string representations of all instances based on the class name.
- `update` - Updates an instance based on the class name and ID by adding or updating attributes (saves the change into the JSON file).

### `models/` Directory

This directory contains classes used for this project, such as:

- `base_model.py` - The `BaseModel` class from which future classes will be derived.
  - `__init__(self, *args, **kwargs)` - Initialization of the `BaseModel`.
  - `__str__(self)` - String representation of the `BaseModel` class.
  - `save(self)` - Updates the `updated_at` attribute with the current datetime.
  - `to_dict(self)` - Returns a dictionary containing all keys/values of the instance.

#### Classes Inherited from `BaseModel`:

- `amenity.py`
- `city.py`
- `place.py`
- `review.py`
- `state.py`
- `user.py`

### `models/engine/` Directory

This directory contains the `FileStorage` class, which handles JSON serialization and deserialization:

- `file_storage.py` - Serializes instances to a JSON file and deserializes them back to instances.
  - `all(self)` - Returns the dictionary `__objects`.
  - `new(self, obj)` - Sets in `__objects` the object with a key of `obj.id`.
  - `save(self)` - Serializes `__objects` to the JSON file (path: `__file_path`).
  - `reload(self)` - Deserializes the JSON file to `__objects`.

### `tests/` Directory

The `tests` directory contains all unit test cases for this project:

- `test_models/test_base_model.py` - Contains the `TestBaseModel` and `TestBaseModelDocs` classes.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_base_model(self)` - Test that `models/base_model.py` conforms to PEP8.
  - `test_pep8_conformance_test_base_model(self)` - Test that `tests/test_models/test_base_model.py` conforms to PEP8.
  - `test_bm_module_docstring(self)` - Test for the `base_model.py` module docstring.
  - `test_bm_class_docstring(self)` - Test for the `BaseModel` class docstring.
  - `test_bm_func_docstrings(self)` - Test for the presence of docstrings in `BaseModel` methods.

#### `TestBaseModel` class:

- `test_is_base_model(self)` - Test that the instantiation of a `BaseModel` works.
- `test_created_at_instantiation(self)` - Test that `created_at` is a public instance attribute of type `datetime`.
- `test_updated_at_instantiation(self)` - Test that `updated_at` is a public instance attribute of type `datetime`.
- `test_diff_datetime_objs(self)` - Test that two `BaseModel` instances have different datetime objects.

- `test_models/test_amenity.py` - Contains the `TestAmenityDocs` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_amenity(self)` - Test that `models/amenity.py` conforms to PEP8.
  - `test_pep8_conformance_test_amenity(self)` - Test that `tests/test_models/test_amenity.py` conforms to PEP8.
  - `test_amenity_module_docstring(self)` - Test for the `amenity.py` module docstring.
  - `test_amenity_class_docstring(self)` - Test for the `Amenity` class docstring.

- `test_models/test_city.py` - Contains the `TestCityDocs` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_city(self)` - Test that `models/city.py` conforms to PEP8.
  - `test_pep8_conformance_test_city(self)` - Test that `tests/test_models/test_city.py` conforms to PEP8.
  - `test_city_module_docstring(self)` - Test for the `city.py` module docstring.
  - `test_city_class_docstring(self)` - Test for the `City` class docstring.

- `test_models/test_file_storage.py` - Contains the `TestFileStorageDocs` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_file_storage(self)` - Test that `models/file_storage.py` conforms to PEP8.
  - `test_pep8_conformance_test_file_storage(self)` - Test that `tests/test_models/test_file_storage.py` conforms to PEP8.
  - `test_file_storage_module

_docstring(self)` - Test for the `file_storage.py` module docstring.
  - `test_file_storage_class_docstring(self)` - Test for the `FileStorage` class docstring.

- `test_models/test_place.py` - Contains the `TestPlaceDoc` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_place(self)` - Test that `models/place.py` conforms to PEP8.
  - `test_pep8_conformance_test_place(self)` - Test that `tests/test_models/test_place.py` conforms to PEP8.
  - `test_place_module_docstring(self)` - Test for the `place.py` module docstring.
  - `test_place_class_docstring(self)` - Test for the `Place` class docstring.

- `test_models/test_review.py` - Contains the `TestReviewDocs` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_review(self)` - Test that `models/review.py` conforms to PEP8.
  - `test_pep8_conformance_test_review(self)` - Test that `tests/test_models/test_review.py` conforms to PEP8.
  - `test_review_module_docstring(self)` - Test for the `review.py` module docstring.
  - `test_review_class_docstring(self)` - Test for the `Review` class docstring.

- `test_models/state.py` - Contains the `TestStateDocs` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_state(self)` - Test that `models/state.py` conforms to PEP8.
  - `test_pep8_conformance_test_state(self)` - Test that `tests/test_models/test_state.py` conforms to PEP8.
  - `test_state_module_docstring(self)` - Test for the `state.py` module docstring.
  - `test_state_class_docstring(self)` - Test for the `State` class docstring.

- `test_models/user.py` - Contains the `TestUserDocs` class.
  - `setUpClass(cls)` - Set up for the doc tests.
  - `test_pep8_conformance_user(self)` - Test that `models/user.py` conforms to PEP8.
  - `test_pep8_conformance_test_user(self)` - Test that `tests/test_models/test_user.py` conforms to PEP8.
  - `test_user_module_docstring(self)` - Test for the `user.py` module docstring.
  - `test_user_class_docstring(self)` - Test for the `User` class docstring.

## Examples of Use

Here are some examples of how to use the AirBnB Clone CLI:

```shell
vagrantAirBnB_clone$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  all  create  destroy  help  quit  show  update

(hbnb) all MyModel
** class doesn't exist **
(hbnb) create BaseModel
7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) all BaseModel
[[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}]
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}
(hbnb) destroy BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
** no instance found **
(hbnb) quit
```

## Bugs

No known bugs at this time.

## Authors

- [Alexa Orrico - Github / Twitter](https://github.com/alexaorrico)
- [Jennifer Huang - Github / Twitter](https://github.com/)
- [Jhoan Zamora - Github / Twitter](https://github.com/)
- [David Ovalle - Github / Twitter](https://github.com/)

Second part of Airbnb: Joann Vuong

## License

This project is in the public domain and has no copyright protection.
