# Alert on missing metrics

Is it possible to alert on non existing datapoints?

### Author:

Brian Demant <brian.demant@gmail.com>

Using the solution provided by [juliusv](github.com/juliusv) on [#prometheus](https://webchat.freenode.net/?channels=#prometheus)

### Problem: 

Sometimes it's not enough to alert on low/high value, but also if the value is not provided at all.

For example if:

- a service is supposed to provide a metric
- a service has gone out of use (no one calls it anymore)

### Solution:

We got following alert rule: sum(rate(something_processed_total[5m])) < 75 
 

	absent(sum(rate(something_processed_total[5m]))) or absend(something_processed_total)
	

	ALERT IF my_metric_name{job="foo"} unless on(job, instance) (up{job="foo"} == 1) ...


### TODO

- Test solution in RL