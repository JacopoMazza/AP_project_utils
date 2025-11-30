# AP Project Sequence Diagrams


## Planet Initialization

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant P as Planet AI

    O->>P: StartPlanetAI
    P->>O: StartPlanetAIResult(planet_id, timestamp)
```

## Planet AI Stop

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant P as Planet AI

    O->>P: StopPlanetAI
    P->>O: StopPlanetAIResult(planet_id, timestamp)
```

## Sunray Interaction

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant P as Planet AI

    O->>P: Sunray(Sunray)
    P->>O: SunrayAck(planet_id, timestamp)
```

## Asteroid Defense Scenario

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant P as Planet AI

    O->>P: Asteroid(Asteroid)
    P->>O: AsteroidAck(planet_id, Option<Rocket>, timestamp)
```

## Internal State Discovery

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant P as Planet

    O->>P: InternalStateRequest
    P->>O: InternalStateResponse(planet_id, PlanetState, timestamp)
```

## Explorer Initialization

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant E as Explorer

    O->>E: StartExplorerAi
    E->>O: StartExplorerAIResult(explorer_id, timestamp)
```

## Stop Explorer

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant E as Explorer

    O->>E: StopExplorerAI
    E->>O: StopExplorerAIResult(explorer_id, timestamp)
```

## Neighbors discovery

```mermaid
sequenceDiagram
    participant E as Explorer
    participant O as Orchestrator

    E->>O: NeighborsRequest(explorer_id, current_planet_id, timestamp)
    O->>E: NeighborsResponse(Vec<planet_id>)
```

## Moving to another planet (Manually from Orch)

```mermaid
sequenceDiagram
    participant E as Explorer
    participant O as Orchestrator

    O ->> E: MoveToPlanet(channel_of_new_planet)
    E->> O: MovedToPlanetResult(explorer_id, timestamp)
```

## Moving to another planet (Explorer Asks)

```mermaid
sequenceDiagram
    participant E as Explorer
    participant O as Orchestrator

    E->>O: TravelToPlanet(explorer_id, start_planet_id, dst_planet_id)
    O ->>E: MoveToPlanet(Option<channelof_new_planet>)
     E->> O: MovedToPlanetResult(explorer_id, timestamp)
```
## Bag Content 

```mermaid
sequenceDiagram
    participant O as Orchestrator
    participant E as Explorer

    O->>E: BagContentRequest
    E->>O: BagContentResponse(explorer_id, Box<dyn Bag>, timestamp)
```

## Basic Resource discovery(manually)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI
    participant O as Orchestrator

    O ->> E: SupportedResourceRequest
    E ->> P: SupportedResourceRequest(explorer_id)
    P ->> E: SupportedResourceResponse(resource_list)
    E ->> O: SupportedResourceResponse(resource_list, explorer_id, timestamp)
```
## Combination Rules discovery(manually)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI
    participant O as Orchestrator

    O ->> E: SupportedCombinationRequest
    E ->> P: SupportedCombinationRequest(explorer_id)
    P ->> E: SupportedCombinationResponse(comb_list)
    E ->> O: SupportedCombinationResponse(comb_list, explorer_id, timestamp)
```
## Basic Resource Generation(manually)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI
    participant O as Orchestrator

    O ->> E: GenerateResourceRequest(res_to_generate)
    E ->> P: GenerateResourceRequest(explorer_id, res_to_generate)
    P ->> E: GenerateResourceResponse(Option<BasicResource>)
    E ->> O: GenerateResourceResponse(Option<BasicResource>, explorer_id, timestamp)
```

##  Resource Combination(manually)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI
    participant O as Orchestrator

    O ->> E: CombineResourceRequest(CombineResourceRequest)
    E ->> P: CombineResourceRequest(CombineResourceRequest, explorer_id)
    P ->> E: CombineResourceResponse(Option<ComplexResource>)
    E ->> O: CombineResourceResponse(Option<ComplexResource>, explorer_id)
```

## Basic Resource discovery (from Explorer)

```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI

    E ->> P: SupportedResourceRequest(explorer_id)
    P ->> E: SupportedResourceResponse(resource_list)
```

## Combination Rules discovery(from Explorer)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI

    E ->> P: SupportedCombinationRequest(explorer_id)
    P ->> E: SupportedCombinationResponse(comb_list)

```

## Basic Resource Generation (from Explorer)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI

    E ->> P: GenerateResourceRequest(explorer_id, res_to_generate)
    P ->> E: GenerateResourceResponse(Option<BasicResource>)
```


##  Resource Combination(from Explorer)
```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI

    E ->> P: CombineResourceRequest(CombineResourceRequest, explorer_id)
    P ->> E: CombineResourceResponse(Option<ComplexResource>)

```

## Energy Cell Availability

```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet AI

    E->>P: AvailableEnergyCellRequest(explorer_id)
    P->>E: AvailableEnergyCellResponse(available_cells_qty)
```


## Internal State Discovery (from Explorer)

```mermaid
sequenceDiagram
    participant E as Explorer
    participant P as Planet

    E->>P: InternalStateRequest(explorer_id)
    P->>E: InternalStateResponse(PlanetState)
```

