[![Apache Sling](https://sling.apache.org/res/logos/sling.png)](https://sling.apache.org)

&#32;[![Build Status](https://ci-builds.apache.org/job/Sling/job/modules/job/sling-org-apache-sling-jcr-maintenance/job/master/badge/icon)](https://ci-builds.apache.org/job/Sling/job/modules/job/sling-org-apache-sling-jcr-maintenance/job/master/)&#32;[![Test Status](https://img.shields.io/jenkins/tests.svg?jobUrl=https://ci-builds.apache.org/job/Sling/job/modules/job/sling-org-apache-sling-jcr-maintenance/job/master/)](https://ci-builds.apache.org/job/Sling/job/modules/job/sling-org-apache-sling-jcr-maintenance/job/master/test/?width=800&height=600)&#32;[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=apache_sling-org-apache-sling-jcr-maintenance&metric=coverage)](https://sonarcloud.io/dashboard?id=apache_sling-org-apache-sling-jcr-maintenance)&#32;[![Sonarcloud Status](https://sonarcloud.io/api/project_badges/measure?project=apache_sling-org-apache-sling-jcr-maintenance&metric=alert_status)](https://sonarcloud.io/dashboard?id=apache_sling-org-apache-sling-jcr-maintenance)&#32;[![JavaDoc](https://www.javadoc.io/badge/org.apache.sling/org.apache.sling.jcr.maintenance.svg)](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.jcr.maintenance)&#32;[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.apache.sling/org.apache.sling.jcr.maintenance/badge.svg)](https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.apache.sling%22%20a%3A%22org.apache.sling.jcr.maintenance%22)&#32;[![jcr](https://sling.apache.org/badges/group-jcr.svg)](https://github.com/apache/sling-aggregator/blob/master/docs/groups/jcr.md) [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)


# Apache Sling JCR Maintenance

This project provides reference implementation of Maintenance jobs for maintaining a Apache Jackrabbit OAK repository in Apache Sling.

This includes the following Maintenance jobs:

- [DataStoreCleanupScheduler](src/main/java/org/apache/sling/jcr/maintenance/internal/DataStoreCleanupScheduler.java) - Run the [RepositoryManagementMBean.startDataStoreGC(true)](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/api/jmx/RepositoryManagementMBean.html#startDataStoreGC-boolean-) method to perform a Garbage Collection of the Data Store
- [RevisionCleanupScheduler](src/main/java/org/apache/sling/jcr/maintenance/internal/RevisionCleanupScheduler.java) - Run the [RepositoryManagementMBean.startRevisionGC()](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/api/jmx/RepositoryManagementMBean.html#startRevisionGC--) method to perform a Garbage Collection of the Revision Store
- [VersionCleanup](src/main/java/org/apache/sling/jcr/maintenance/internal/VersionCleanup.java) - Job to traverse the JCR Version Store
  and remove versions (oldest-first) exceeding a configurable limit

As well as a [Health Check](src/main/java/org/apache/sling/jcr/maintenance/internal/RepositoryMaintenanceHealthCheck.java) to ensure the jobs are scheduled and have not failed.

## Configuration

To see a reference implementation, see the [Configuration Feature](src/main/features/configuration.json).

## Features

There are two primary features made by this project include:

- **Base** - org.apache.sling:org.apache.sling.jcr.maintenance:slingosgifeature:base:${project.version} - only the bundle and service user
- **Default** - org.apache.sling:org.apache.sling.jcr.maintenance:slingosgifeature:default:${project.version} - the bundle, service user and default configuration which keeps 5 versions and runs the jobs every night

This module is part of the [Apache Sling](https://sling.apache.org) project.
