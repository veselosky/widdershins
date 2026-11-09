# Developer Documentation

- [Architecture Overview](architecture.md)

Widdershins is architected as a system, not just an application. It manages a user's personal space on the web, and participates in the social web using open federation protocols like ActivityPub.

The system consists of multiple processes and storage areas. All the web serving processes can and should be fronted by a CDN to improve performance and scalability. The system is designed to scale down to a single user on a single (and not very powerful) server, and scale up to thousands of users on multiple servers.

The main service components built into Widdershins are:

- ownersuite -- The web control center allowing users to administer their personal web space.
- inbox -- The ActivityPub inbox for receiving activities from other users and services. The inbox is divided into web workers and background workers. Web workers handle incoming requests and background workers process the activities in the inbox.
- fedimail -- The ActivityPub outbox for sending activities to other federated services. The fedimail service also has both web workers and background workers. Web workers handle message submissions while background workers handle delivery.
- mediaproxy -- A proxy for serving and caching media files from other servers.
- ssg -- A static site generator transforms canonical content into static files in multiple formats for serving to the public web.

The storage areas in Widdershins each serve a specific purpose:

- public -- The public web space for serving static files to the public web. This is where the static site generator outputs its files.
- media -- The media storage area for storing media files uploaded by users.
- staticfiles -- The static files storage area for storing static files used by the web application, such as CSS, JavaScript, and images.
- private -- The private storage area for storing canonical data files.
- cache -- Cache storage area used by mediaproxy.
- database -- The database storage area for storing structured data used to manage the web application.
