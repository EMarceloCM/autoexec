# Configurações do CS2 fora do autoexec

O `autoexec.cfg` não controla vídeo, driver nem Windows. Abaixo está o que é configurado à mão.

**PC:** i7-7700 · GTX 1060 6GB · 16 GB DDR4-2400 (dual channel) · AOC 24G4 1080p 180 Hz
**Resolução:** 1280x960, 4:3 esticado

## Vídeo no jogo

| Opção | Valor |
|---|---|
| Modo de exibição | Tela cheia |
| Proporção / Resolução | Normal 4:3 · 1280x960 |
| Taxa de atualização | 180 Hz |
| V-Sync | Desativado |
| MSAA | 2x (4x se sobrar GPU) |
| Qualidade global de sombras | Média |
| Sombras dinâmicas | Todas |
| Detalhe de modelo/textura | Baixo |
| Filtragem de texturas | Trilinear |
| Detalhe de shaders | Baixo |
| Detalhe de partículas | Baixo |
| Oclusão de ambiente | Desativada |
| HDR | Desempenho |
| FidelityFX Super Resolution | Desativado (qualidade máxima) |
| NVIDIA Reflex | Ativado |

> Brilho e contraste dos jogadores vêm do autoexec.
> Se faltar FPS: Sombras dinâmicas → Apenas luz solar; depois Sombras → Baixa. O FSR fica sempre desligado.

## Painel de Controle NVIDIA

**Esticado** (Exibição → Ajustar tamanho e posição da área de trabalho):
- Dimensionamento: Tela cheia
- Executar em: GPU
- Substituir o modo definido por jogos e programas: marcado

**3D → Configurações de programa → cs2.exe:**
- Gerenciamento de energia: Preferir desempenho máximo
- Modo de baixa latência: Desligado (o Reflex do jogo assume)
- Sincronização vertical: Desligado
- Filtragem de textura – qualidade: Alto desempenho

## Windows

- Plano de energia: Alto desempenho. Comando: ```powercfg /setactive 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c ```
- Modo de Jogo: Ativado
- Jogos → Capturas → Gravar o que aconteceu: Desativado

## Steam

Opções de inicialização:

```
-nojoy -freq 180 +exec autoexec.cfg
```

## Onde ficam os arquivos (para backup)

- Autoexec: `D:\SteamLibrary\steamapps\common\Counter-Strike Global Offensive\game\csgo\cfg\autoexec.cfg`
- Vídeo: `C:\Program Files (x86)\Steam\userdata\<SteamID>\730\local\cfg\cs2_video.txt`

## Impedir que o vídeo resete

O NVIDIA App com otimização automática ligada sobrescreve o `cs2_video.txt` (volta para 16:9 e gráficos altos).

1. NVIDIA App → Gráficos → ⋮ → desligar a otimização automática de jogos.
2. Deixar o `cs2_video.txt` como somente leitura:

```
attrib +r "C:\Program Files (x86)\Steam\userdata\<SteamID>\730\local\cfg\cs2_video.txt"
```

Para mudar o vídeo: `attrib -r` no arquivo, ajustar no jogo, fechar o CS2 e rodar `attrib +r` de novo.
