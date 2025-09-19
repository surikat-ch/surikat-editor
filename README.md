# surikat-editor
Homeassistant extension

Build : 
docker build -t surikat-editor .

Launch :
docker run -d -p 8000:8000 --name surikat-instance surikat-editor

Build local : 
docker build --build-arg BUILD_FROM=python:3.11-slim -t surikat-editor .

DEV
docker build -f Dockerfile.dev -t surikat-editor .
docker run -p 8000:8000 surikat-editor



CheatSheet

# config.yml
name: "My Example Add-on"
version: "1.0.0"
slug: "my_example_addon"
description: "Addon showing all schema option types"
startup: services
boot: auto
arch:
  - amd64
  - armv7
  - aarch64
map:
  - config:rw
  - share:rw
  - media:ro
options:
  string_option: "default text"
  int_option: 42
  float_option: 3.14
  bool_option: false
  list_option:
    - "item1"
    - "item2"
  dict_option:
    key1: "value1"
    key2: 123
  select_option: "option1"
  port_option: 8080
  device_option: "/dev/ttyUSB0"

schema:
  string_option: str
  int_option: int
  float_option: float
  bool_option: bool
  list_option:
    - str
  dict_option:
    key1: str
    key2: int
  select_option: list(option1|option2|option3)
  port_option: port
  device_option: device
