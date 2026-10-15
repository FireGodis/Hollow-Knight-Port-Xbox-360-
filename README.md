# Hollow Knight — estudo de recuperação e compatibilidade

> Projeto não oficial em Unity, baseado em uma exportação local feita com AssetRipper. O nome do repositório registra uma meta; **não existe port para Xbox 360 nem compatibilidade validada**.

![Status](https://img.shields.io/badge/status-em%20diagn%C3%B3stico-orange) ![Unity](https://img.shields.io/badge/Unity-6000.0.61f1-black?logo=unity)

## Estado atual

| Área | Situação observada |
|---|---|
| Editor | Unity `6000.0.61f1`, Windows, Direct3D 11 |
| Execução | Menu, abertura e tutorial carregam no Editor |
| Menu `Menu_Title` | Fundo e logotipo principal ausentes; alguns textos e elementos menores aparecem |
| Abertura `Opening_Sequence` | Vídeo aparece como uma faixa estreita à esquerda; há aviso de timestamps H.264 |
| Gameplay `Tutorial_01` | Cenário majoritariamente preto, forma azul clara fora de posição e personagem invisível |
| Console nas capturas | Sem contador de erros vermelhos; avisos presentes |
| Port Xbox 360 | Não iniciado nem validado |

## Problema visual em investigação

As capturas mais recentes continuam mostrando os mesmos defeitos. Já foram tentados rebuild de sprites e tilemaps TK2D, ajustes de bounds e mistura alfa nos shaders `Sprites/Default-ColorFlash` e `Sprites/Cherry-Default`. **Essas tentativas não corrigiram a imagem**, então a causa principal segue aberta.

A imagem-fonte do título existe e está ligada ao objeto `LogoTitle`; a cena também usa câmeras separadas para conteúdo, HUD e fundo. Uma sonda temporária foi preparada **apenas na cópia local** para registrar em Play Mode câmeras, renderers, bounds e dimensões do vídeo ao carregar cada cena afetada. Ela ainda aguarda uma execução no Editor; não há causa raiz confirmada nem correção visual validada.

1. Capturar os valores efetivos de projeção, viewport, máscara, posição e renderers nas três cenas.
2. Comparar vértices, UVs e bounds das malhas TK2D com a região visível na captura.
3. Conferir o plano e a proporção do clipe na abertura.
4. Aplicar uma alteração por vez e validar menu, abertura e tutorial; compilação sozinha não confirma a correção.

## Abrir a cópia local

A cópia Unity de trabalho fica em `ExportedProject/`. Abra **essa pasta** no Unity `6000.0.61f1`. As imagens deste README refletem as capturas enviadas durante a investigação; não provam que os defeitos foram resolvidos.

## Conteúdo deste repositório

Este repositório público contém documentação e regras contra envio acidental de conteúdo extraído. A exportação completa, os assets originais e o código descompilado ficam apenas na máquina de trabalho e estão excluídos pelo `.gitignore`.

O repositório **não contém** uma build jogável, o projeto Unity completo, arquivos de Hollow Knight ou uma implementação para Xbox 360.

## Plano de trabalho

- [ ] Determinar por que os elementos principais não aparecem ou ficam fora de posição.
- [ ] Corrigir a abertura para preencher o enquadramento esperado.
- [ ] Restaurar personagem e cenário no tutorial.
- [ ] Validar as três cenas no Editor e numa build de teste para Windows.
- [ ] Só então avaliar a viabilidade técnica de um port para Xbox 360.

## Aviso de direitos

Hollow Knight, personagens, nomes, código, imagens, áudio e demais assets pertencem aos respectivos titulares. Este é um projeto de estudo não oficial. Não redistribua material protegido sem autorização dos titulares. “Xbox 360” descreve uma intenção futura, não afiliação, licença ou compatibilidade confirmada.