# documentation tools

Tools used for generating documentation based on [plantuml](https://plantuml.com/) and [mkdocs](https://www.mkdocs.org/).

## Usage

## plantuml

* Generate svg from plantuml files in a given directory and output to  specific target directory
  ```docker run -v $PWD:/sources -u $(id -u ${USER}):$(id -g ${USER}) --rm bridgefield/plantuml /sources/docs/diagrams/* -o /sources/docs/images/generated -tsvg```

### mkdocs

* Create new mkdocs project
  ```docker run -v $PWD:/sources -u $(id -u ${USER}):$(id -g ${USER})  --rm bridgefield/mkdocs new /sources```
* Build html documentation from mkdocs project
  ```docker run -v $PWD:/sources -u $(id -u ${USER}):$(id -g ${USER})  --rm bridgefield/mkdocs build -f /sources/mkdocs.yml -t readthedocs```
