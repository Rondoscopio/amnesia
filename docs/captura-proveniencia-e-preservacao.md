# Captura, proveniência e preservação de evidências

Este documento registra diretrizes e requisitos em discussão para a Amnésia, sistema de monitoramento, coleta e memória documental do Rondoscópio. As funcionalidades descritas são propostas para avaliação e não representam recursos já implementados.

## Finalidade e limites

A Amnésia deve registrar acontecimentos e documentos com fidelidade técnica e preservar o contexto disponível, inclusive quando sua relevância investigativa ainda não seja conhecida. Seu papel é fornecer material rastreável para verificações futuras. Ela não deve atribuir intenção, culpa, causalidade ou favorecimento aos envolvidos.

Uma captura pode demonstrar que determinado conteúdo foi obtido por um método específico em determinado momento, dentro dos limites desse método. Não demonstra por si só a veracidade das alegações contidas na publicação, a autoria intelectual, a intenção de quem publicou ou a permanência da informação no servidor.

O valor histórico de um registro pode surgir muito tempo depois da captura. A seleção de materiais não deve depender exclusivamente de hipóteses investigativas atuais, mas respeitar critérios de interesse público, proporcionalidade, direitos de terceiros e retenção legal.

## Preservação do material original

- Preservar os bytes originais obtidos, evitando substituí-los por versões corrigidas, transcritas ou comprimidas.
- Registrar URL inicial e final, redirecionamentos, método, código de resposta, protocolo HTTP, cabeçalhos pertinentes e horários de requisição e resposta.
- Distinguir o corpo HTTP recebido da página renderizada após execução de JavaScript. Guardar ambos quando necessário e tecnicamente possível.
- Preservar, quando aplicável, capturas de tela, recursos carregados, documentos anexos, áudio, vídeo, imagens e dados estruturados.
- Considerar WARC para preservar recursos e transações de navegação e armazenamento de objetos para os arquivos originais.
- Armazenar no MongoDB metadados, identificadores, relações de captura e referências aos arquivos. Avaliar armazenamento externo para objetos grandes e não depender de um único documento BSON para todo o material.
- Registrar formato, tamanho, hash criptográfico, localização do objeto, política de acesso, versão da captura e identificador estável.
- Não modificar o original quando houver nova captura do mesmo endereço. Preservar versões e relacionar sucessões, exclusões, retificações e alterações observadas.

## Proveniência da conexão

Sempre que a origem for HTTPS e a tecnologia empregada permitir, registrar na própria conexão que recebeu o recurso:

- Hostname, SNI, endereço IP remoto, porta, DNS consultado e informações sobre proxies ou intermediários conhecidos.
- Versão TLS efetivamente negociada e cipher suite selecionada.
- ALPN, grupo de troca de chaves e outras informações de negociação quando disponíveis.
- Certificado de servidor apresentado e cadeia de certificados recebida, preferencialmente com os bytes DER ou PEM originais.
- Impressões digitais SHA-256 dos certificados, sujeito, emissor, nomes alternativos, número de série, período de validade e informações relevantes à validação.
- Resultado da validação da cadeia de confiança e correspondência do nome do servidor, inclusive falhas e exceções.
- Identificação da ferramenta, biblioteca, versão, configuração e ambiente usados para capturar a conexão.

Separar os dados da conexão efetiva dos resultados obtidos em consultas posteriores. Uma nova conexão pode terminar em outro servidor, certificado ou nó de CDN. Não atribuir metadados de uma conexão auxiliar à captura original.

Um certificado TLS autentica a conexão conforme as garantias e limitações do protocolo, mas não constitui assinatura digital do conteúdo de uma página. A existência de TLS válido, isoladamente, não prova que um documento foi produzido por determinada pessoa ou estava disponível naquele endereço em uma data histórica.

## Integridade, temporalidade e cadeia de custódia

- Calcular hashes SHA-256 dos arquivos preservados e dos registros relevantes.
- Criar manifesto verificável que associe o material, metadados, hashes, identificadores de captura e seus relacionamentos.
- Definir representação canônica do manifesto antes de calcular o seu hash, evitando diferenças causadas apenas pela serialização.
- Avaliar assinatura digital do manifesto e carimbo do tempo confiável, por exemplo com RFC 3161.
- Registrar diferentes horários e suas origens, como instante declarado pelo servidor, horário observado pelo coletor e carimbo externo. Não tratá-los como equivalentes.
- Manter trilha de operações, acessos relevantes, transformações, operadores e versões do software de captura.
- Avaliar mecanismos de retenção imutável ou resistentes a adulteração e cópias independentes e verificáveis.
- Documentar o procedimento de verificação e recuperação dos arquivos e manifestos ao longo do tempo.

O carimbo do tempo atesta propriedades temporais do material submetido à autoridade conforme sua política, mas não certifica a veracidade do conteúdo. O MongoDB não deve ser considerado, isoladamente, um cofre imutável.

## Derivados multimodais e possibilidade de análise futura

O acervo pode incluir textos, fotos, mapas, anúncios, gravações, sinais e documentos. O valor de um detalhe pode só ser identificado posteriormente. Por exemplo, um nome ou logotipo de patrocinador pouco destacado em fotografia antiga pode se tornar pertinente para investigar relações identificadas anos depois.

- Preservar as imagens e gravações originais antes de gerar derivados.
- Permitir resultados adicionais de OCR, transcrição, reconhecimento de logotipos, detecção de objetos, extração de entidades, indexação, descrições e busca semântica.
- Identificar cada derivado por ferramenta, modelo, versão, parâmetros, data, arquivo de origem e confiança ou limitações quando aplicáveis.
- Registrar separadamente observação direta, metadados declarados, resultados automatizados e validação humana.
- Permitir reprocessamento posterior com modelos melhores sem reescrever as capturas originais.
- Não considerar uma identificação automatizada de pessoa, marca, voz ou entidade como fato confirmado sem verificação adequada.
- Adotar salvaguardas proporcionais para biometria, dados pessoais, informações sensíveis e riscos de identificação incorreta.

## Verificação independente e preservação responsável

Capturas feitas por operadores ou ambientes independentes podem auxiliar na corroboração, desde que sua origem, método e horários sejam registrados. Várias observações concordantes não eliminam, por si só, hipóteses alternativas, erro compartilhado ou manipulação na fonte.

Aplicar controle de acesso, minimização de dados, política de retenção, proteção de fontes e medidas contra divulgação indevida. Interesse público não dispensa análise jurídica ou proteção de terceiros. O requisito de preservar histórico não significa retenção irrestrita ou permanente de todos os dados.

## Relação com o Córtex

A Amnésia preserva observações e seus derivados rastreáveis. O [Córtex](https://github.com/Rondoscopio/cortex/blob/main/docs/analise-temporal-e-interpretacao.md) formula hipóteses, reconstrói acontecimentos, investiga relações e revê interpretações ao longo do tempo. Uma conclusão posterior deve referenciar os registros que a sustentam e não alterar o material original.

## Pontos de avaliação tecnológica

- WARC e ferramentas de captura HTTP e de navegador.
- Extração de detalhes TLS a partir da conexão efetiva e preservação da cadeia X.509.
- Hashes, manifestos, assinatura digital e carimbo do tempo.
- MongoDB para metadados e armazenamento de objetos para originais.
- Versionamento, observabilidade, auditoria de acesso e preservação distribuída.
- OCR, transcrição e extração multimodal com proveniência de derivados.
- Procedimentos de validação, reprodutibilidade e proteção de dados.

As decisões de implementação dependerão de testes, avaliação de custo, requisitos de segurança e análise jurídica.
