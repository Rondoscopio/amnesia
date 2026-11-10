# Cadastro de eventos e organização do acervo fotográfico

Este documento registra requisitos propostos para a Amnésia. O módulo ainda não está implementado. Seu objetivo é permitir a catalogação de eventos e a associação de fontes, documentos e registros multimodais, preservando contexto histórico e rastreabilidade.

## Eventos como objetos documentais

O evento deve ter identidade própria, independente de qualquer fotografia, notícia ou publicação. O cadastro deve aceitar eventos únicos, recorrentes e desdobramentos como sessões e reuniões vinculadas.

Informações previstas para o evento:

- Identificador estável, título, descrição, tipo e situação de verificação.
- Datas e horários anunciados, efetivos e de publicação da informação, sempre com fuso horário e precisão conhecida.
- Local físico, endereço, município, coordenadas quando justificadas e modalidade presencial, virtual ou híbrida.
- Entidades responsáveis pela organização, realização, apoio e divulgação.
- Pautas anunciadas, temas previstos, programação, painéis, apresentações, assuntos efetivamente tratados e eventuais alterações.
- Convidados, palestrantes, mediadores, autoridades, representantes, organizadores e outros papéis atribuídos pelas fontes.
- Participantes, presença relatada ou comprovada, comparecimento parcial e ausência confirmada quando houver fonte confiável.
- Patrocinadores e apoiadores, natureza do apoio e período relevante, sem presumir contribuição financeira.
- Documentos oficiais, convites, cartazes, fotografias, gravações, transcrições, atas, notícias, publicações e páginas que sustentam as informações.
- Histórico de alterações, autoria dos cadastros, revisões e referências a registros originais.

Cada campo sujeito a controvérsia deve admitir múltiplas afirmações com suas próprias fontes, horários de conhecimento, graus de verificação e possíveis divergências. Uma agenda anunciada não comprova que a atividade ocorreu como previsto.

## Participação e relações documentadas

A plataforma deve distinguir os estados e papéis, evitando tratar convidados como presentes ou pessoas fotografadas como organizadores:

- Convidado identificado em convite ou programa.
- Presença anunciada ou confirmada por terceiros.
- Participação declarada pelo próprio interessado.
- Presença registrada por documento, ata ou testemunho verificável.
- Pessoa visível em mídia, ainda sem identificação ou confirmação de presença no evento.
- Organizador, palestrante, mediador, patrocinador, apoiador e outros papéis específicos.
- Participação contestada, não confirmada ou desconhecida.

Um nome em um cartaz não garante comparecimento. Uma pessoa visível ao fundo de uma fotografia não comprova participação ativa, relação pessoal, concordância com a pauta ou envolvimento em decisões.

As pessoas e organizações poderão ter identificadores próprios e nomes históricos. O vínculo com um evento deve trazer papel, intervalo temporal, origem da informação e status de validação, sem formar automaticamente conclusões investigativas.

## Patrocínios, organizações e evidências de contexto

O cadastro deve diferenciar patrocinador, apoio institucional, parceiro, expositor, organizador, anunciante e fornecedor. Quando possível, registrar a fonte da classificação, o instrumento que documenta a relação, o período e a natureza monetária ou não monetária do vínculo.

Nomes, logotipos e marcas presentes em fotografias antigas podem adquirir relevância posterior. A Amnésia deverá permitir associar a região de uma imagem a uma entidade candidata, registrar leitura por OCR ou anotação manual e preservar a fotografia original.

A identificação de um logotipo em um evento anterior não comprova, por si só, favorecimento, relação pessoal ou conexão causal com contrato público posterior. Essas hipóteses devem ser investigadas pelo [Córtex](https://github.com/Rondoscopio/cortex/blob/main/docs/analise-temporal-e-interpretacao.md).

## Acervo fotográfico e audiovisual

Organização semelhante à experiência de busca do Google Fotos, sem presumir que todas as suas tecnologias ou práticas sejam adequadas ao Rondoscópio:

- Exibir galeria por data, evento, local, fonte e coleções.
- Permitir associar fotos, vídeos e trechos de gravação a um ou vários eventos.
- Manter os arquivos originais, metadados de captura, hashes, autoria, licenças e procedência.
- Distinguir data de captura, data do evento, data da publicação e data de ingestão.
- Permitir marcação manual de pessoas, logotipos, placas, objetos, textos e regiões de interesse da imagem.
- Identificar versões, duplicatas exatas e imagens visualmente semelhantes sem apagar os originais.
- Indexar textos extraídos por OCR, descrições acessíveis, transcrições e metadados verificáveis.
- Permitir corrigir associações e desfazer classificações mantendo o histórico de alterações.
- Oferecer pesquisa combinada por evento, participante documentado, período, local, organização, texto em imagem e tipo de mídia.

A captura de imagens deve respeitar direitos autorais, privacidade, limites de acesso e normas pertinentes. Disponibilidade pública de uma fotografia não equivale a autorização irrestrita para tratamento biométrico.

## Rostos: detecção, agrupamento e identificação

Existem três operações diferentes, com implicações técnicas e jurídicas distintas:

1. **Detecção de rosto:** localizar a região de uma face em uma fotografia, sem associá-la a uma identidade.
2. **Agrupamento de rostos semelhantes:** localizar imagens que possivelmente mostram a mesma pessoa, ainda sem afirmar quem é ela.
3. **Identificação de pessoa:** associar um grupo ou imagem a uma identidade nominal, com fontes, justificativa e verificação humana.

O Google Fotos utiliza grupos de rostos semelhantes que podem receber marcadores, permitindo corrigir agrupamentos. Isso é uma referência de experiência do usuário, não uma autorização para reproduzir reconhecimento biométrico indiscriminado.

O agrupamento baseado em modelos faciais deve permanecer como capacidade condicionada à análise jurídica, de riscos e de necessidade. Não se deve ativar por padrão uma busca biométrica massiva de pessoas presentes em eventos públicos.

Caso exista fundamento legal e avaliação favorável para uma aplicação delimitada:

- Isolar as funções biométricas das funções gerais de cadastro, galeria e OCR.
- Restringir finalidade, fontes, grupos de pessoas e universo de comparação.
- Evitar a formação de uma base indiscriminada de rostos de espectadores, transeuntes ou menores.
- Restringir acesso aos modelos biométricos, às imagens de referência e às correspondências.
- Proteger dados biométricos com medidas específicas de segurança e retenção.
- Registrar modelo, versão, parâmetros, limiares, escopo, resultado e eventuais falsos positivos.
- Exigir revisão humana antes de associar nominalmente pessoas a fotos com base em reconhecimento automatizado.
- Permitir desfazer agrupamentos, contestar identidades, corrigir associações e atender direitos dos titulares.
- Não disponibilizar ferramenta pública de identificação facial ou consulta biométrica aberta.
- Não inferir presença em um evento unicamente de um resultado biométrico sem validação contextual.
- Documentar finalidade, hipótese legal aplicável, necessidade, proporcionalidade e avaliação de impacto quando cabível.

Dados biométricos vinculados a uma pessoa são dados pessoais sensíveis segundo a LGPD, sujeitos a condições específicas de tratamento. A fonte ser pública não elimina essas obrigações. Referências para avaliação incluem a [ANPD](https://www.gov.br/anpd/pt-br/acesso-a-informacao/perguntas-frequentes) e a [ajuda do Google Fotos sobre agrupamento de rostos](https://support.google.com/photos/answer/6128838?hl=pt-BR_ALL).

## Modelo conceitual inicial

O desenho físico do banco de dados permanece em aberto. Como entidades lógicas, considerar:

- **Evento:** título, tipo, datas, local, descrição, situação e relações com outros eventos.
- **Pauta:** tema, posição na programação, horário, fontes e mudanças.
- **Entidade:** pessoa, organização, instituição ou grupo, com nomes e identificadores históricos.
- **Participação:** relação entre entidade e evento, papel, estado de comprovação, intervalo e fontes.
- **Patrocínio ou apoio:** relação com tipo e natureza documentada, vigência, fontes e eventuais divergências.
- **Registro:** arquivo ou captura preservada com proveniência, integridade e níveis de acesso.
- **Anotação de mídia:** localização de região, texto, objeto, logotipo ou observação vinculada a registro.
- **Grupo visual:** conjunto de itens visualmente semelhantes, sem identidade necessariamente atribuída.
- **Afirmação e fonte:** o que uma fonte sustenta, quando, com qual escopo e resultado de verificação.

A Amnésia deve representar relações entre eventos e registros sem substituir os bytes originais ou misturar hipóteses analíticas com fatos documentados. O Córtex poderá consumir esses vínculos para reconstruir cronologias e investigar relações históricas.

## Fluxo de cadastro proposto

1. Cadastrar ou importar um evento a partir de uma fonte identificada.
2. Registrar local, horário, pauta, organização, convidados e patrocinadores como afirmações documentadas.
3. Associar documentos, imagens e gravações aos seus arquivos originais preservados.
4. Extrair texto, marcas e objetos em mídia como candidatos à anotação.
5. Validar manualmente as associações relevantes, sobretudo identidades e papéis de pessoas.
6. Registrar correções, versões e divergências sem apagar o histórico documental.
7. Permitir consultas históricas e exportação dos dados, respeitando limites de acesso.

## Critérios mínimos de aceitação

- [ ] Criar, editar, versionar e relacionar eventos e sessões.
- [ ] Cadastrar pautas, convidados, participantes, locais, organizadores, patrocinadores e apoios.
- [ ] Associar cada informação relevante à fonte e ao estado de verificação.
- [ ] Distinguir convite, presença anunciada, presença documentada e identificação ainda incerta.
- [ ] Vincular eventos a fotografias, vídeos, áudios, atas e páginas preservadas.
- [ ] Pesquisar o acervo por datas, eventos, entidades, locais e textos extraídos.
- [ ] Anotar manualmente regiões de imagens e revisar resultados automatizados.
- [ ] Manter rastreabilidade de correções, versões, modelos e responsáveis.
- [ ] Documentar e avaliar os riscos legais antes de qualquer função biométrica.
- [ ] Não atribuir identidade automaticamente nem disponibilizar busca facial pública.
- [ ] Integrar com as diretrizes de [captura e proveniência](captura-proveniencia-e-preservacao.md).
