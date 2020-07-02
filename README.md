[![Contributors][contributors-shield]][contributors-url]
[![Issues][issues-shield]][issues-url]
[![workflow status][workflow-shield]][workflow-url]

# fastapi-tdd-docker

## Table of Contents

- [About](#about)
  - [Built With](#built-with)
- [Installation](#installation)
- [Usage](#usage)
- [Tests](#tests)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## About

**fastapi-tdd-docker** is a code-along (with minor differences) to the course **[Test-Driven Development with FastAPI and Docker][tddfastapi]** by Michael Herman.

### Built With

- Docker & Docker Compose
- [FastAPI](https://fastapi.tiangolo.com/)

## Installation

#### Prerequisites:

- Python 3.6+
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

#### 1. Clone the repository:

```bash
$ git clone git@github.com:sophiabrandt/fastapi-tdd-docker.git && cd fastapi-tdd-docker
```

#### 2. Use Docker and Docker Compose

```bash
$ docker-compose up -d --build
```

#### 3. Apply Migrations

```bash
$ docker-compose exec web python app/db.py
```

## Usage

```bash
$ docker-compose up -d
```

Go to [`http://localhost:8002/docs`](http://localhost:8002/docs).

## Tests

```bash
$ docker-compose exec web python -m pytest
```

Unit Tests with Monkey-patching:

```bash
$ docker-compose exec web pytest -k "unit" -n auto
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

Copyright © 2020 Michael Herman.

Please see the [original repo](https://github.com/testdrivenio/fastapi-tdd-docker) for details.

## Acknowledgments

- [Michael Herman](https://mherman.org/)

[contributors-shield]: https://img.shields.io/github/contributors/sophiabrandt/fastapi-tdd-docker.svg?style=flat-square
[contributors-url]: https://github.com/sophiabrandt/fastapi-tdd-docker/graphs/contributors
[issues-shield]: https://img.shields.io/github/issues/sophiabrandt/fastapi-tdd-docker.svg?style=flat-square
[issues-url]: https://github.com/sophiabrandt/fastapi-tdd-docker/issues
[workflow-shield]: https://github.com/sophiabrandt/fastapi-tdd-docker/workflows/Continuous%20Integration%20and%20Delivery/badge.svg?style=flat-square&branch=master
[workflow-url]: https://gitlab.com/sophiabrandt/fastapi-tdd-docker/commits/master
[tddfastapi]: https://testdriven.io/courses/tdd-fastapi/
