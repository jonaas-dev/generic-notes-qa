<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Logging practices I follow](#logging-practices-i-follow)
  - [Not all logs are equal / Should you even log it?](#not-all-logs-are-equal--should-you-even-log-it)
  - [How to log it?](#how-to-log-it)
    - [Log levels TLDR](#log-levels-tldr)
    - [Log frugality](#log-frugality)
      - [What you should do instead?](#what-you-should-do-instead)
    - [Log uniqueness](#log-uniqueness)
    - [Summary](#summary)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Logging practices I follow

Font: https://www.16elt.com/2023/01/06/logging-practices-I-follow/

## Not all logs are equal / Should you even log it?

- Is this log really needed? does it rely important information I couldn’t get from the other logs in the same flow?
- Am I going to log an object that can be huge on production? If so, can I just log a few metrics of that objects instead? for example, it’s length, or handpick a few important attribute to log.
- Does the information I am about to log will help me to debug/understand the flow?

## How to log it?

### Log levels TLDR

- `ERROR`: Parts of the flow failed, we want to send alerts to our on-call for this failures.
- `WARNING`: Doesn’t necessarily point to a failure, but an unexpected behavior that should be investigated.
- `INFO`: Record major events in the flow to help the developer reading it understand what was being executed.
- `DEBUG`: Like INFO but more detailed, including inspection into objects, data structures, etc.

### Log frugality

Whatever service you are using for logging, **it costs money**, and a fast way to burn money is to log the entire json object that was relatively small on your dev env, but blew up on production.

#### What you should do instead?

- Pick the attributes that are the most important and useful to log, the attributes that will actually help you debug the continuation of the flow.
- Sometimes, you just need to know if the object is empty or not, just log that - not the entire object.

### Log uniqueness

Each log message in the system should be unique.

### Summary
...