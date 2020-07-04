## JQ Tool to parse Json content
**jq** is a lightweight and flexible command-line JSON processor. jq is like sed for JSON data - you can use it to slice and filter and map and transform structured data with the same ease that sed, awk, grep and friends let you play with text
> jq as a replacement for sed/grep for JSON

## Command
> jq - commandline JSON processor [version 1.5-1-a5b5cbe]
Usage: jq [options] <jq filter> [file...]

        jq is a tool for processing JSON inputs, applying the
        given filter to its JSON text inputs and producing the
        filter's results as JSON on standard output.
        The simplest filter is ., which is the identity filter,
        copying jq's input to its output unmodified (except for
        formatting).
        For more advanced filters see the jq(1) manpage ("man jq")
        and/or https://stedolan.github.io/jq

        Some of the options include:
         -c             compact instead of pretty-printed output;
         -n             use `null` as the single input value;
         -e             set the exit status code based on the output;
         -s             read (slurp) all inputs into an array; apply filter to it;
         -r             output raw strings, not JSON texts;
         -R             read raw strings, not JSON texts;
         -C             colorize JSON;
         -M             monochrome (don't colorize JSON);
         -S             sort keys of objects on output;
         --tab  use tabs for indentation;
         --arg a v      set variable $a to value <v>;
         --argjson a v  set variable $a to JSON value <v>;
         --slurpfile a f        set variable $a to an array of JSON texts read from <f>;
        See the manpage for more options.

## Example
### Search Content
Assume you have below json as a file content.json

    {
      "apiVersion": "v1",
      "kind": "Pod",
      "metadata": {
        "labels": {
          "app": "myapp"
        },
        "name": "myapp",
        "namespace": "project1"
      },
      "spec": {
        "containers": [
          {
            "command": [
              "sleep",
              "3000"
            ],
            "image": "busybox",
            "imagePullPolicy": "IfNotPresent",
            "name": "busybox"
          },
          {
            "name": "nginx",
            "image": "nginx",
            "resources": {},
            "imagePullPolicy": "IfNotPresent"
          }
        ],
        "restartPolicy": "Never"
      }
    }

To read node spec, just use below command
`jq .spec content.json`

    {
      "containers": [
        {
          "command": [
            "sleep",
            "3000"
          ],
          "image": "busybox",
          "imagePullPolicy": "IfNotPresent",
          "name": "busybox"
        },
        {
          "name": "nginx",
          "image": "nginx",
          "resources": {},
          "imagePullPolicy": "IfNotPresent"
        }
      ],
      "restartPolicy": "Never"
    }

### Beautify json content
Assume you have content2.json with content
{"person":{"name":"Natarajan","nationality":"Indian","city":"Bangalore"}}

To Beautify, please use below command
jq '.' content2.json

    {
      "person": {
        "name": "Natarajan",
        "nationality": "Indian",
        "city": "Bangalore"
      }
    }
