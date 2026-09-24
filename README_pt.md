# HelixCraft

**Software desktop de apoio à engenharia genética com IA** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · **Português** · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft é um software desktop voltado à pesquisa em biologia molecular e engenharia genética.
> Ele cobre o fluxo de trabalho completo "encontrar o gene → ler a sequência → desenhar a clonagem →
> montar in silico → validar no experimento → gerenciar os dados": edição de mapas de vetores,
> análise de sequências, desenho de primers, simulação de digestão por enzimas de restrição e de
> eletroforese em gel, fluxos de trabalho de clonagem, análise de cromatogramas de sequenciamento,
> consulta a dados de espécies, análise de proteínas e um assistente de IA opcional. Todos os dados
> ficam armazenados no seu próprio computador — sem cadastro de conta e sem dependência de nuvem. A
> interface está disponível em 20 idiomas.
> Documentação completa: [简体中文](README.md) · [English](README_EN.md)

## O que você pode fazer

- Abriu o arquivo de um plasmídeo? Veja com clareza a composição de elementos e os sítios de restrição e exporte a figura do mapa em qualidade de publicação;
- Simule de ponta a ponta, no computador, um plano Gibson / Golden Gate / digestão-ligação antes de preparar qualquer reação;
- Desenhe primers de clonagem ou primers de qPCR que atravessam junções de exons, com pontuações e evidências de avaliação;
- Confira cromatogramas de sequenciamento, monte leituras (reads) e alinhe os resultados de volta ao vetor recombinante para verificação;
- Anote canais (lanes) e bandas em fotos de gel e faça a análise quantitativa;
- A partir de uma sequência proteica, analise propriedades físico-químicas, localização subcelular, sítios de modificação e estrutura tridimensional;
- Organize vetores, genes, primers e arquivos de sequenciamento por projeto, transfira entre computadores do laboratório e mantenha backups regulares.

## Download

A versão mais recente está sempre no [**canal Releases · latest**](releases/tag/latest):

| Plataforma | Instalador | Como instalar |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Duplo clique para executar o assistente de instalação |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Duplo clique para entregar ao instalador gráfico do sistema, ou `sudo apt install ./<arquivo>` |

O canal latest também é a fonte de dados do "verificar atualizações" dentro do aplicativo, com os arquivos substituídos a cada versão. Versões anteriores ficam na [lista de Releases](releases), cada uma com seu próprio arquivamento. O `latest.json` na mesma pasta lista nome, tamanho em bytes e resumo SHA-256 de cada instalador, permitindo conferir se o download está completo e intacto.

## Instalação

### Windows

- Dê um duplo clique em `HelixCraft.Setup.<version>.exe` e siga o assistente (requer Windows 10 ou superior, x64; por padrão instala para todos os usuários e pede privilégios de administrador).
- O assistente oferece um componente opcional de **dados de exemplo** (vetores de exemplo, fluxos de trabalho de clonagem e plugins de espécies) para facilitar o primeiro contato; os exemplos só são importados quando o conteúdo correspondente ainda não existe e **nunca sobrescrevem os dados que você já criou**.
- **Instalar por cima preserva todos os dados existentes.** O diretório de dados é `%APPDATA%\HelixCraft` (os sub-bancos de dados de espécies ficam em `%APPDATA%\HelixCraftData`) e a desinstalação não o remove.

### Linux (Debian / Ubuntu, x86_64)

- O duplo clique no `.deb` entrega a instalação ao instalador gráfico do sistema (GNOME Software / App Center / KDE Discover / GDebi); comando equivalente no terminal: `sudo apt install ./helixcraft_<version>_amd64.deb`.
- O programa é instalado em `/opt/HelixCraft`, os dados do usuário ficam em `~/.config/HelixCraft` e **a desinstalação não remove os dados**.
- Recomenda-se ter fontes CJK instaladas no sistema (o pacote declara `Recommends: fonts-noto-cjk`; instalar com `dpkg -i` não resolve as dependências — prefira `apt install`).

## Atualização online

Cerca de 20 segundos após a inicialização, o aplicativo verifica atualizações em segundo plano (ativado por padrão, no máximo uma vez a cada 24 horas, podendo ser desativado nas configurações). Ao encontrar uma versão nova, ele apenas avisa — **nada é baixado automaticamente**. O download usa HTTPS, com retomada de transferência e verificação SHA-256; no Windows a instalação é concluída pelo assistente NSIS com reinício automático do aplicativo, e no Linux o `.deb` baixado é entregue ao instalador de software do sistema.

## Principais funcionalidades

- **Mapa de vetores e edição de sequência**: visões circular e linear totalmente vinculadas ao texto da sequência; elementos coloridos por tipo, com sítios de restrição, pareamento de primers, ORFs e marcações de mutação sobrepostos; estilos personalizáveis e exportação em SVG / PDF / PNG; edição direta por digitação, exclusão e colagem, com coordenadas reajustadas automaticamente e 50 passos de desfazer/refazer.
- **Anotação inteligente**: compara o vetor completo com o banco de elementos para reconhecer automaticamente elementos conhecidos (identidade de DNA ≥99% ou tradução ≥90%, com prévia item a item antes da importação em lote) e infere campos como resistência a antibióticos, hospedeiro, promotor e gene repórter, sempre com confiança, evidências e sem sobrescrever o que já existe.
- **Predição de ORFs e busca BLAST online**: varredura nas seis molduras de leitura (inclusive ORFs que cruzam a origem em plasmídeos circulares), com resultado clicável no mapa, e submissão da sequência selecionada ao NCBI (blastn / blastp / blastx etc.).
- **Simulação de digestão e eletroforese virtual**: fragmentos em tempo real para digestões simples, duplas e múltiplas, com sítios sobre a origem tratados corretamente; o resultado vai para o gel simulado com 11 marcadores comuns, concentração de agarose, voltagem e tempo de corrida, segundo modelos de migração calibrados pela literatura; checagem automática dos efeitos de metilação (Dam / Dcm / CpG) e assistente para escolher os sítios de restrição.
- **Tela de fluxos de trabalho de clonagem**: monte o experimento como um fluxograma, com 30 tipos de nós de saída calculada em tempo real (fontes de sequência → desenho de primers / otimização de códons → PCR virtual → digestão / purificação → montagem → transformação / PCR de colônia / verificação por sequenciamento → salvar no banco); estratégias Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, com bases protetoras), ligação com T4, TA / TOPO, Gateway LR / BP e BioBrick; desfazer/refazer, salvamento automático e importação/exportação JSON.
- **Tela de construção molecular (Beta)**: desenho no estilo "escolha o backbone e preencha com elementos" — o aplicativo gera a estratégia de linearização, todas as sequências de primers, o sistema de montagem, os fragmentos esperados na PCR de colônia e os primers de sequenciamento sugeridos; o produto só entra no banco se for idêntico base a base ao desenho.
- **Desenho de primers (geral e qPCR)**: três modos e mais de 50 parâmetros ajustáveis, com 20 principais candidatos avaliados por Tm, GC%, risco de hairpin/dímero e nota de 0 a 100; o assistente de qPCR faz o alinhamento de splicing entre mRNA e genoma e prioriza primers sobre junções de exons para evitar interferência do DNA genômico, com pontuação de conformidade MIQE; PCR in silico para qualquer par de primers e banco de primers com importação/exportação Excel e histórico de alterações.
- **Análise de sequenciamento**: visualizador de cromatogramas AB1 com conferência base a base contra a referência; montagem automática de leituras Sanger pelo algoritmo CAP3, com sequência consenso, profundidade de cobertura e avisos de regiões de baixa qualidade; alinhamento das leituras contra o seu vetor recombinante, com diagrama colorido por conservação (mismatches, inserções e deleções evidentes); também com alinhamento múltiplo (ClustalW) e árvores filogenéticas.
- **Análise de imagens de gel com IA**: modelo de aprendizado profundo integrado identifica canais e bandas automaticamente (com ajuste manual); informados o canal do marcador e a quantidade de uma banda de referência, a curva-padrão de tamanhos dá o tamanho do fragmento e a quantidade de DNA de cada banda (densidade óptica integrada); exporta figuras anotadas (PNG / JPG / BMP / TIF) e resultados em JSON.
- **Análise de proteínas**: três vistas vinculadas — diagrama de topologia, painel de sequência de aminoácidos e estrutura 3D carregada do RCSB PDB / AlphaFold DB; análises locais em segundos (peso molecular, ponto isoelétrico, hidrofobicidade, composição aminoacídica, localização subcelular, sete classes de sítios de modificação pós-traducional etc.) e refinamento online com InterProScan e BLAST, que apenas acrescenta anotações verificadas do Swiss-Prot, nunca sobrescreve.
- **Gestão de dados de laboratório**: cinco bancos de dados (vetores, sequências, primers, enzimas com 580+ enzimas de restrição e projetos); compartilhamento de grupos de trabalho inteiros em um único arquivo `.hcvec`, transferência criptografada entre computadores na mesma rede local por código de pareamento de 8 dígitos, backup automático na inicialização e exclusão sempre precedida da lista de dados afetados.
- **Assistente de IA (opcional)**: funciona com qualquer endpoint compatível com OpenAI (a chave de API fica só na sua máquina); interpreta textos de protocolos de clonagem e opera o próprio software — as alterações seguem o mesmo caminho da edição manual e podem ser desfeitas —, mas nunca produz uma única base; sem IA configurada, todos os recursos mantêm caminho 100% manual.

## Plugins de dados de espécies

Anotações e dados de expressão chegam por "plugins de espécies", que podem ser instalados, ativados e desinstalados na página de configurações. O instalador já traz a anotação do arroz (cerca de 100 mil registros), e tudo o que for obtido online é salvo automaticamente no cache local, permanecendo disponível offline. Fontes disponíveis por plugin:

| Plugin | Fontes de dados | O que você obtém |
|---|---|---|
| Arroz (Rice) | RAP-DB, MSU-RGAP, RiceData, RiceXPro | anotações de lócus gênicos, estrutura de exons, sinônimos, fenótipos de mutantes, mapas de expressão espaço-temporal (valores + imagens), sequências de todas as versões e conversão de IDs entre bases |
| Ensembl Plants | Ensembl Plants, EBI Expression Atlas | busca de genes em mais de 100 espécies, download de sequências, anotações GO e expressão RNA-Seq |
| Phytozome | JGI Phytozome | busca de genes, modelos gênicos, sequências CDS / cDNA / proteicas, domínios e genes homólogos |
| ePlant (BAR) | BAR eFP Browser | pictogramas coloridos de expressão tecidual e níveis de expressão por tecido para 13 espécies |

## Segurança e privacidade dos dados

- **Todos os dados ficam no seu computador**: nada é enviado a servidores; a rede só é usada quando você pede dados online (NCBI, bancos de dados de espécies, repositórios de estruturas proteicas, atualizações do software).
- **A IA é totalmente opcional**: o assistente depende de uma chave de API sua, guardada apenas na sua máquina; sem configurar IA, todos os recursos mantêm caminho manual completo.
- **Mesclar nunca sobrescreve**: dados de exemplo, pacotes importados e transferências recebidas pela rede local apenas preenchem campos vazios e não tocam no conteúdo existente.

## Formatos de arquivo suportados

| Sentido | Formatos |
|---|---|
| Abrir / importar | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), cromatogramas (`.ab1`), Excel de primers (`.xlsx`), anotações proteicas (UniProtKB / GFF3 / InterProScan / GenPept), estruturas proteicas (PDB / mmCIF) e pacotes HelixCraft (pacote de genes / vetores `.hcvec` / proteínas `.hcp`) |
| Salvar / exportar | GenBank, FASTA, SnapGene `.dna`, EMBL, figuras de mapas (SVG / PDF / PNG / JPG / BMP / TIF), figuras de gel anotadas, Excel de primers, anotações proteicas em 6 formatos, pacotes de genes / `.hcvec` / `.hcp`, página web estática do gene e backup completo em ZIP |

## Idiomas da interface

Desde a v0.3.7, todos os módulos funcionais têm tradução completa em 20 idiomas: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština. Troque a qualquer momento em "Configurações → Idioma"; a primeira tela do instalador também permite escolher o idioma.

## Sobre este repositório

Este repositório serve apenas para **distribuir instaladores e o manifesto de atualização online** e não contém o código-fonte. O Release da tag `latest` é o canal de atualização online (arquivos substituídos a cada versão); as tags `v<version>` arquivam as versões históricas. O mesmo repositório é hospedado em sincronia no [GitHub](https://github.com/liudab/HelixCraft) e no [GitCode](https://gitcode.com/BohanLab/HelixCraft), com instaladores publicados nos dois.

## Licença

[MIT](LICENSE)

## Contato

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
