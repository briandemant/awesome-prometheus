# Labels pr Target group

Labeling differently on multiple target_group 

### Author:

Brian Demant <brian.demant@gmail.com>

Using the solution provided by [juliusv](github.com/juliusv) on [#prometheus](https://webchat.freenode.net/?channels=#prometheus)

### Problem: 

Only having one job scraping every node and wanting to add label in the config.

So that it is possible to group front and backend servers with labels

### Solution:

```yaml
scrape_config:
  job_name: "myjobname"
  # ...
  target_groups:
    - targets: [...]
      labels:
        group: production
        foo: bar
    - targets: [...]
      labels:
        group: development
        foo: baz
```