# Core Middleware

Channel-to-core services for Jamuna Bank PLC. Split by concern: customer API, account API, and notification API. A channel calls the service that matches the job. It does not open a core session of its own.

This repository is a sanitized public sample.

## What I owned

I split the core facade into three APIs on purpose. Notification is chatty and allowed to fail. Customer lookup is not. If they shared a process, a bad SMS gateway would have taken enquiry down with it.

## Technologies

- .NET
- Customer API
- Account API
- Notification API
- SQL and core drivers
- Used with the Kafka consumer when a result must come back asynchronously

## Features

- Customer lookup facade
- Account inquiry facade
- Notification dispatch after a booking or a status change
- Health of each API independent
- No core host and no notification provider key in this repository

## Design choice

Three deployable units. The channel still sees one family of contracts. I would rather restart notification than bounce account enquiry.

Related: [JamunaConnect](https://github.com/rafiimam/jbl-jamunaconnect), [Event Consumer](https://github.com/rafiimam/jbl-event-consumer)

Portfolio: https://rafiimam.github.io/rafi_portfolio/
