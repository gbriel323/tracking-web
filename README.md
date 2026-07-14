# Plataforma de Rastreamento por Vídeo

## Visão Geral

A Plataforma de Rastreamento por Vídeo foi desenvolvida para facilitar o rastreamento de produtos por meio da captura e análise de evidências em vídeo. Utilizando uma arquitetura robusta baseada na AWS e implementando tecnologias como RTSP e FFmpeg, o sistema garante eficiência e confiabilidade na rastreabilidade de eventos relacionados a produtos.

## Objetivo do Projeto

O principal objetivo é:

- **Rastrear produtos**: Relacionar movimentações de produtos a operadores, horários e câmeras utilizadas, criando um histórico completo de eventos.
- **Independência de fabricantes**: O sistema deve ser compatível com diversos fabricantes de câmeras, permitindo a utilização de equipamentos comuns de mercado, como Intelbras, Hikvision, Dahua, Axis e câmeras RTSP.
- **Solução escalável**: A arquitetura está preparada para suportar um número elevado de câmeras e eventos, garantido pela separação entre o processamento local e a gestão na nuvem.

## Arquitetura da Solução

A arquitetura é dividida em duas camadas principais:

1. **AWS Cloud**: Responsável pelo gerenciamento de todo o negócio, incluindo empresas, lojas, usuários, produtos e operações. A comunicação entre os sistemas ocorre através do API Gateway, que integra Lambda Functions para processar as requisições de forma segura e eficiente.

2. **Video Agent**: Opera localmente, dentro das lojas, e é responsável pela comunicação RTSP, captura de vídeo e geração de evidências. O Video Agent não se comunica diretamente com os serviços da AWS, garantindo segurança e controle sobre os dados.

## Comunicação e Fluxo de Dados

A comunicação entre os componentes do sistema implica em várias etapas:

- O **Video Agent** captura o vídeo e o segmenta para posterior análise.
- Os dados coletados são enviados ao **API Gateway**, garantindo que toda interação com a nuvem seja realizada através de pontos de acesso seguros.
- O **Sync Worker** é encarregado de sincronizar dados quando a conectividade é restabelecida, permitindo a operação offline.

## Benefícios da Plataforma

- **Baixo custo**: A arquitetura foi projetada para minimizar custos operacionais, evitando chamadas desnecessárias à nuvem.
- **Escalabilidade**: Suporte a múltiplas lojas e empresas, facilitando a expansão da plataforma.
- **Facilidade de manutenção**: Separa as responsabilidades, permitindo que atualizações e melhorias sejam realizadas sem afetar o sistema como um todo.
- **Preparação para SaaS**: O design modular torna o sistema preparado para serviços em ambiente SaaS, expandindo seu alcance e acessibilidade.

## Roadmap do Projeto

O projeto será desenvolvido em várias sprints, com entregas focadas em cada etapa da implementação, desde a gravação RTSP até a criação de um dashboard para consulta de eventos.

- **Sprint 1**: Gravação RTSP
- **Sprint 2**: Indexer
- **Sprint 3**: Integração com AWS
- **Sprint 4**: Eventos
- **Sprint 5**: Geração de Evidências
- **Sprint 6**: Upload para S3
- **Sprint 7**: Dashboard para visualização e relatórios.

## Conclusão

A arquitetura da Plataforma de Rastreamento por Vídeo oferece uma solução inovadora que combina o gerenciamento na nuvem com análise local de vídeo. Isso possibilita uma operação eficiente e independente do fabricante das câmeras, criando uma poderosa ferramenta para empresas que buscam controle e auditoria de produtos.

---

**Status do Projeto**
- SQLite local ✅
- SyncWorker ✅
- API Gateway ✅
- Lambda Recording API ✅
- DynamoDB TTL 50 dias ✅
- Separação Cloud/Agent ✅
