# Let's Take The Bridge Pattern To The Next Level

This video covers how the bridge pattern works and why it's useful. To spice things up, I'm going to deviate from the classic definition of the pattern from the Gang-of-four book (which is already quite powerful) and show you a couple of things you can do in Python to shorten the code and at the same time allow for extra flexibility.

Here's the link to the video: https://youtu.be/mM2-FPm1EhI.

# Class diagrams

## Original bridge pattern

```mermaid
classDiagram
    class Abstraction {
        <<abstract>>
    }
    RefinedAbstraction1 --|> Abstraction
    RefinedAbstraction2 --|> Abstraction
    class Implementation {
        <<abstract>>
        +implementation()
    }
    Abstraction o-- Implementation : uses
    Implementation <|-- ConcreteImplementation1
    Implementation <|-- ConcreteImplementation2
    ConcreteImplementation1: +implementation()
    ConcreteImplementation2: +implementation()
```

## Streaming devices and services example

```mermaid
classDiagram
    class StreamingService  {
        <<abstract>>
        +start_stream()
        +stop_stream()
        +fill_buffer()
    }
    YouTubeStreamingService --|> StreamingService
    TwitchStreamingService --|> StreamingService
    class Device {
        <<abstract>>
        +get_buffer_data()
    }
    StreamingService o-- Device : uses
    Device <|-- Webcam
    Device <|-- DSLRCamera
    Webcam: +get_buffer_data()
    DSLRCamera: +get_buffer_data()
```
