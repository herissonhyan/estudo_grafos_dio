# 🎬 Movie & Series Graph Database

## Overview
Este grafo representa um universo de **filmes, séries, usuários, atores, diretores e gêneros**, permitindo análises de comportamento de usuários, conexões entre atores e filmes, e exploração de padrões de gênero.  
O grafo é implementado em **Neo4j** usando **Cypher**, com `MERGE` para evitar duplicações de nós e relacionamentos.

---

## Nodes (Nós)

| Label       | Descrição |
|------------|-----------|
| `Viewer`   | Usuários que assistem filmes ou séries. Cada nó possui a propriedade `name`. |
| `Movie`    | Filmes. Cada nó possui a propriedade `title`. |
| `Series`   | Séries. Cada nó possui a propriedade `title`. |
| `Actor`    | Atores. Cada nó possui a propriedade `name`. |
| `Director` | Diretores. Cada nó possui a propriedade `name`. |
| `Genre`    | Gêneros de filmes e séries. Cada nó possui a propriedade `type`. |

---

## Relationships (Relacionamentos)

| Relationship        | Direção | Descrição | Propriedades |
|-------------------|---------|-----------|--------------|
| `WATCHED`         | Viewer → Movie/Series | Indica que o usuário assistiu ao conteúdo | `rating` (1–5) |
| `ACTED_IN`        | Actor → Movie/Series | Indica que o ator atuou no conteúdo | — |
| `DIRECTED`        | Director → Movie/Series | Indica que o diretor dirigiu o conteúdo | — |
| `IN_GENRE`        | Movie/Series → Genre | Associa o conteúdo ao seu gênero | — |

---

## Gêneros incluídos

- `Drama`  
- `Sci-Fi`  
- `Action`  
- `Comedy`  

---

## Usuários e avaliações

- 8 usuários (`Alice`, `Bob`, `Carla`, `Diego`, `Emily`, `Fábio`, `Gina`, `Hugo`)  
- Cada usuário assiste a **1 ou 2 conteúdos**.  
- Cada `WATCHED` possui uma avaliação (`rating`) de 3 a 5.  
- Permite análises de **preferência de usuários**, recomendação de conteúdo e clusterização de perfis.

---

## Conteúdos incluídos

- **Filmes:** Titanic, Inception, The Matrix, Dark Knight, Forrest Gump, La La Land, The Godfather  
- **Séries:** The 100, Stranger Things, Friends  

---

## Atores e Diretores

Exemplos de conexões:

- Leonardo DiCaprio atuou em Titanic  
- Kate Winslet atuou em Titanic  
- Christopher Nolan dirigiu Inception e Dark Knight  
- Keanu Reeves atuou em The Matrix  
- Matthew Perry atuou em Friends  
- Millie Bobby Brown atuou em Stranger Things  

*(Podem ser adicionados mais atores e diretores para enriquecer o grafo.)*

---

## Possíveis análises

1. **Recomendações de filmes e séries:**  
   - Baseado em usuários com perfis semelhantes (`WATCHED` e `rating`).  

2. **Análise de comunidades (community detection):**  
   - Encontrar grupos de usuários com gosto semelhante.  
   - Descobrir clusters de filmes por gênero ou atores em comum.  

3. **Exploração de rede de atores e diretores:**  
   - Visualizar conexões entre atores que trabalharam juntos.  
   - Identificar diretores mais influentes.  

4. **Estatísticas gerais:**  
   - Conteúdo mais assistido  
   - Avaliações médias por gênero  
   - Popularidade de séries vs filmes  

---

## Observações técnicas

- **Cypher `MERGE`** foi usado para evitar duplicação de nós ou relacionamentos.  
- Cada nó possui **uma chave única natural** (`name` para pessoas, `title` para conteúdo, `type` para gênero).  
- O grafo pode ser expandido facilmente com novos usuários, filmes, séries, atores, diretores e gêneros.  
