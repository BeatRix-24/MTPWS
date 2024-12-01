**Multi-Threaded Proxy Server in C**

This project implements a multi-threaded proxy server in C, leveraging semaphores, threading, and caching to efficiently handle multiple client requests. The UML diagram below illustrates the workflow of the proxy server.



**Project Theory**

A proxy server acts as an intermediary between a client and a server. It receives client requests, processes them (including caching and concurrency), and forwards them to the intended server. This project implements such a server with multi-threading to handle multiple clients simultaneously.
Basic Working Flow

    The client sends a request to the proxy server.
    If the request is valid, the proxy server creates a new thread to handle the request.
    The server checks the cache:
        Cache Hit: Responds to the client directly from the cache.
        Cache Miss: Forwards the request to the main server, stores the response in the cache, and sends it back to the client.
    Semaphores (sem_wait() and sem_post()) ensure thread synchronization and prevent race conditions.
    Threads are managed using pthread_join() and pthread_exit().

Why Semaphores?

    Unlike condition variables, semaphores do not require passing thread-specific parameters.
    They simplify thread synchronization and ensure mutual exclusion.

Key Features

    Caching: Speeds up repeated requests using an LRU cache.
    Concurrency: Manages multiple clients using threads.
    Request Handling: Supports GET requests and handles cache validation.

Motivation

This project was designed to explore:

    The flow of HTTP requests between clients and servers.
    Concurrency mechanisms like semaphores and thread management.
    Implementation of an efficient caching mechanism for performance improvement.

Limitations

    URLs with multiple dynamic clients may create redundant cache entries.
    Fixed cache size restricts the storage of large web pages.
    The project currently supports only GET requests.
