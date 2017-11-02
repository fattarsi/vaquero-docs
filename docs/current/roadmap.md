<head>
            <meta charset="UTF-8">
            <!--[if IE]><meta http-equiv="X-UA-Compatible" content="IE=edge"><![endif]-->
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Vaquero Getting Started</title>
            <link rel="stylesheet" type="text/css" href="../doc.css">
            <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Open+Sans:300,300italic,400,400italic,600,600italic%7CNoto+Serif:400,400italic,700,700italic%7CDroid+Sans+Mono:400">
                      <link rel='shortcut icon' href='cow.png' type='image/x-icon'/ >
            <style>
                .markdown-body {
                    box-sizing: border-box;
                    min-width: 200px;
                    max-width: 1200px;
                    margin: 0 auto;
                    padding: 25px;
                }
            </style>
</head><article class="markdown-body">

# Roadmap

These are some of the features that are planned for Vaquero.


## User API

The REST API is intended to provide users and operaters insight into the resources available in their Vaquero system as well as the current status.

Vaquero manages the available resource pool of machines with the SoT files. These files describe all of the machines available for Vaquero to manage independant of the actual state. Consider the 2 different scenarios:

### Auto-Provision

You have built out your datacenter with Vaquero to suit your needs. As you add more hardware, you update your SoT and as soon as those changes are made Vaquero begins acting on those changes (or when the hardware is actually available).

The API in this case is merly used for monitoring the boot status of the machines.

### On-demand

This case is similar to above except Vaquero will not immediately provision machines as they become available in the SoT. In this case, viewing available resources and provisioning machines is driven by the API. This scenario is better suited when the user consuming the resources isn't necessarily the same person managing the resources that are available.


### Using the API

The API follows a hierarchy that matches configuration structure. A SoT can have a collection of sites, which can have a collection of clusters, which comprise a collection of hosts. Users can drill down to view details on the resources they are interested.

There is also plans for helper endpoints where an API user doesn't need to know these configuration details and can make a request to filter based on the resources they care about, e.g.:

```
POST /v1/cluster/

{
  'hosts': 3,
  'min_memory': '64G',
  'min_disk': '500G',
  'workflow': 'rhel'
}

```
