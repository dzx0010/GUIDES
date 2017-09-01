# Graphical User Interface for DNA Editing Screens (GUIDES)

**Description**:  Genome-scale CRISPR-Cas9 knockout libraries have emerged as popular tools for unbiased, phenotypic screening but easy-to-use software for designing customized guide RNA libraries has lagged behind. GUIDES is a web application for automated, tissue-specific library design. It integrates on-target scores, expression data, and protein structure into an easily accessible web interface.

  - **Technology stack**: Python/Flask backend with Angular.js front-end.
  - **Status**:  Release (1.0)
  - **Links to production or demo instances**: Hosted on the [Sanjana Lab's](http://guides.sanjanalab.org) website.
  - Recently, library design tools such as CRISPR Library Designer have used on-target efficiency scoring to help automate guide design. In addition to on-target scores, our tool integrates expression data and protein structure, while also providing a more easily accessible web interface.


**Screenshots**:

![](https://raw.githubusercontent.com/sanjanalab/GUIDES/master/Screenshot.png)


## Dependencies

Most of the front-end code is written in Coffeescript. Angular.js is used as a front-end framework.

Redis is used for local storage. Celery is used for background processing.

Static data files which are too large for hosting on GitHub must also be added. Installation is described below.

## Installation

After pulling this repository, change the current directory to the GUIDES root folder.

First, setup a Python [virtual environment](http://docs.python-guide.org/en/latest/dev/virtualenvs/) by executing `virtualenv venv` from the root directory of the repository. Activate the virtual enviornment by executing `source venv/bin/activate`.

Then, install the required Python modules by running `pip install -r requirements.txt`. At this point, the virtual environment can be deactivated by executing `deactivate`.

Next, install node modules by executing `npm install` from the GUIDES root folder.

Next, substitute the folder `static/data` with the `data` folder from the [Sanjana Lab Dropbox]().

Alternatively, run [./install.sh](install.sh) from the GUIDES root folder.

## Usage

Next, open 3 terminal windows. Run the following commands in each window:

```bash
source venv/bin/activate
export DEV=false
export PORT=YOUR_PORT
export SMTPenabled=false
```

To enable emailed summaries of library generation, instead run the following commands in each window:

```bash
source venv/bin/activate
export DEV=false
export PORT=YOUR_PORT
export SMTPenabled=true
export SMTPserver=YOUR_SMTP_SERVER
export SMTPsender=donotreply@YOUR_DOMAIN
export SMTPpassword=YOUR_SMTP_PASSWORD
```

Then, run the following 3 commands, in this order (one in each window):

1. `./run-redis.sh`
2. `celery worker -A app.celery`
3. `./run.sh`

On the [Sanjana Lab](http://guides.sanjanalab.org) website, these commands are run in seperate [Unix screen](http://aperiodic.net/screen/quick_reference)s to enable long-term processing.

## How to test the software

Code for running the tests in our [manuscript]() is located in `static/data/functional_tests`. Some data analysis is required to produce the plots included in our paper.

## Known issues

None currently.

## Getting help

Feel free to reach out to the GUIDES team at [guides-tech@googlegroups.com](mailto:guides-tech@googlegroups.com).

## Getting involved

Please [get in touch](mailto:guides-tech@googlegroups.com) if you are interested in contributing, so we can coordinate our efforts. In particular, we are interested in expanding our tool to include more species.

----

## Open source licensing info
Copyright (c) 2015-2017 Joshua Meier, Feng Zhang and Neville Sanjana. Released under BSD 3. See LICENSE file for details.

If you're interested in getting access to this system under a different license, please contact us.

----
