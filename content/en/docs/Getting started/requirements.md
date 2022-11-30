---
tags: ["installation"]
title: "System Requirements"
linkTitle: "System Requirements"
weight: 10
description: >
  System requirements for the installation.
---

The requirements are fairly standard for a web server running PHP, also on shared hosting.

| Requirement | Version | Details |
| ----------- | ------- | ------- |
| Composer    | >= 2.2  | Composer is the back-end package manager |
| HTTP server |         | Examples: nginx, Apache |
| PHP         | >= 8.1  |         |
| PHP extensions |      | <ul><li>BCMath</li><li>GD</li><li>JSON</li><li>Mbstring</li><li>OpenSSL</li><li>PDO</li><li>XML</li></ul> |
| SQL database |        | Examples: MySQL, MariaDB, PostgreSQL |
| Yarn        | >= 1.20 | Yarn is the front-end package manager. This is strictly not necessary to install on the server as you can build the front-end assets locally as well. |