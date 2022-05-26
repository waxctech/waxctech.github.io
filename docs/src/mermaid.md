# Diagrams as code

- `brew install graphviz`
- [cloud arh](https://diagrams.mingrammer.com/)
- [C4-PlantUM](https://github.com/plantuml-stdlib/C4-PlantUML)
- [plantuml](https://plantuml.com/en/)
- [asciidoc](https://docs.asciidoctor.org/diagram-extension/latest/#meme)
- [VISUALIZATION GRAMMARS](https://vega.github.io/vega/)
- [vega-lite]([https://vega.github.io/vega-lite/)
- [[meraid](https://mermaid-js.github.io/mermaid/#/)

> [output.html]
> additional-js = ["mermaid.min.js", "mermaid-init.js"]

# configure mermaid output dir

> `$mdbook-mermaid install $Repo_DIR/waxctech.github.io/docs`

```mermaid
graph TD;
Z-->B;
A-->C;
B-->D;
C-->D;
```

```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

```mermaid notsupport
gantt
dateFormat  YYYY-MM-DD
title Adding GANTT diagram to mermaid
excludes weekdays 2014-01-10

section A section
Completed task            :done,    des1, 2014-01-06,2014-01-08
Active task               :active,  des2, 2014-01-09, 3d
Future task               :         des3, after des2, 5d
Future task2               :         des4, after des3, 5d
```

```mermaid
gitGraphcommit 
commit
branch develop
commit
commit
commit
checkout main
commit
commit
```

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
```

```mermaid
journey
title My working day
section Go to work
Make tea: 5: Me
Go upstairs: 3: Me
Do work: 1: Me, Cat
section Go home
Go downstairs: 5: Me
Sit down: 5: Me
```

