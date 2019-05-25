# Markdown画图

这是申明一个由左到右水平向右的图

- TB - top bottom
- BT - bottom top
- RL - right left
- LR - left right
- TD - same as TB

```mermaid
graph LR
    A-- text -->B
    A-.-.B
    A-.text.->B
    A==>B
    A===B
    A==text==>B
    A==text===B
    C --- D
    X-.->Y
    E -- This is the label text --- F
    x[This is the text in the box];
    xx(This is the text in the box);
    xxx((This is the text in the circle));
    xxxx>This is the text in the box]
    xxxxx{This is the text in the box}
```

```mermaid
graph TB
        subgraph one
        a1 --> a2
        end
        subgraph two
        b2 --> b2
        end
        subgraph three
        c1 --> c2
        end
        c1 --> a2
```

```mermaid
graph TD
      B["fa:fa-twitter for peace"]
      B-->C[fa:fa-ban forbidden]
      B-->D(fa:fa-spinner);
      B-->E(A fa:fa-camera-retro perhaps?);
```

```mermaid
graph TD
      B["fa:fa-twitter for peace"]
      B-->C[fa:fa-ban forbidden]
      B-->D(fa:fa-spinner);
      B-->E(A fa:fa-camerra-retro perhaps?);


```

```mermaid
graph LR
     id1(Start)-->id2(Stop)
     style id1 fill:#f9f,stroke:#333,stroke-width:4px;
     style id2 fill:#ccf,stroke:#f66,stroke-width:2px,stroke-dasharray:5,5;

```

```mermaid
graph LR
     id1(Start)-->id2(Stop)
     style id1 fill:#f9f,stroke:#333,stroke-width:4px;
     style id2 fill:#ccf,stroke:#f66,stroke-width:2px,stroke-dasharray:5,5;
```

```mermaid
graph LR
      A-->B[AAABBB];
      B-->D;
      class A cssClass;
```

```mermaid
sequenceDiagram
　　　participant Alice
　　　participant Bob
　　　Alice->John:Hello John, how are you?
　　　loop Healthcheck
　　　　　John->John:Fight against hypochondria
　　　end
　　　Note right of John:Rational thoughts <br/>prevail...
　　　John-->Alice:Great!
　　　John->Bob: How about you?
　　　Bob-->John: Jolly good!
```

```mermaid
gantt
　　　dateFormat　YYYY-MM-DD
　　　title Adding GANTT diagram functionality to mermaid
　　　section A section
　　　Completed task　　:done, des1, 2014-01-06,2014-01-08
　　　Active task 　　　　:active, des2, 2014-01-09, 3d
　　　future task 　　　　:　　　  des3, after des2, 5d
　　　future task2　　　　:　　　  des4, after des3, 5d
　　　section Critical tasks
　　　Completed task in the critical line　:crit, done, 2014-01-06,24h
　　　Implement parser and json　　　　　　:crit, done, after des1, 2d
　　　Create tests for parser　　　　　　　:crit, active, 3d
　　　Future task in critical line　　　　　:crit, 5d
　　　Create tests for renderer　　　　　　:2d
　　　Add to ,mermaid　　　　　　　　　　　:1d
```

name | 111 | 222 | 333 | 444
- | :-: | :-: | :-: | -:
aaa | bbb | ccc | ddd | eee|
fff | ggg| hhh | iii | 000|