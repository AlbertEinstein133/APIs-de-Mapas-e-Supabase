# Guia: Criar Vídeo de Demonstração

## Objetivo

Criar um vídeo curto (1-3 minutos) demonstrando as funcionalidades principais da aplicação.

---

## Pré-requisitos

- Smartphone com Android/iOS com a app instalada OU
- Emulador/Simulator rodando a app
- Software para gravar tela:
  - **macOS**: QuickTime (nativo)
  - **Windows**: OBS Studio (gratuito) ou Camtasia
  - **Android**: Screen Recorder (nativo em muitos celulares)
  - **iOS**: Configurações → Controle → Gravador de Tela

---

## Roteiro Recomendado (1-2 minutos)

### Cena 1: Abertura (15 segundos)
```
[Mostrar tela de abertura da app]
Narração: "Esta é uma aplicação de geolocalização que compara três APIs de mapas..."
```

### Cena 2: Demonstrar Geolocalização (20 segundos)
```
[Clique em "📍 Obter Localização Atual"]
[Aguarde a localização ser obtida]
[Mostre as coordenadas na tela]
Narração: "A app obtém a localização atual do usuário com precisão de GPS."
```

### Cena 3: Buscar Endereço (30 segundos)
```
[Mude para Google Maps ou Mapbox]
[Busque por "Avenida Paulista, São Paulo"]
[Selecione um resultado]
[Mostre o endereço e coordenadas]
Narração: "Você pode buscar localizações por endereço usando diferentes APIs."
```

### Cena 4: Ver no Mapa (20 segundos)
```
[Mude entre os provedores: Google Maps, Mapbox, OpenStreetMap]
[Mostre como mudam os detalhes]
Narração: "Escolha entre Google Maps, Mapbox ou OpenStreetMap."
```

### Cena 5: Salvar Localização (25 segundos)
```
[Clique em "💾 Salvar Localização"]
[Veja a localização ser adicionada à lista]
[Role para baixo e mostre a lista de localizações salvas]
Narração: "Salve suas localizações no Supabase e acesse-as depois."
```

### Cena 6: Encerramento (10 segundos)
```
[Mostre a lista de localizações]
[Texto final na tela]
Narração: "Confira o repositório no GitHub para mais detalhes!"
```

**Total: ~2 minutos**

---

## Passo a Passo: Gravar no Emulador/Simulator

### macOS (iOS Simulator)

1. Abra Xcode
2. Rode: `npm run ios`
3. Abra QuickTime Player
4. File → New Screen Recording
5. Selecione o Simulator
6. Clique em Record
7. Realize as ações na app
8. Pare quando terminar
9. File → Save

### Windows/Linux (Android Emulator)

1. Rode: `npm run android`
2. Abra OBS Studio
3. Adicione Source → Display Capture
4. Selecione o emulator
5. Clique em Start Recording
6. Realize as ações na app
7. Clique em Stop Recording
8. Arquivo salvo em `/Videos`

### Seu Smartphone

1. Vá a Configurações → Controle
2. Ative "Gravador de Tela"
3. Abra a app
4. Deslize de cima para baixo (iOS) ou de cima (Android)
5. Clique em "Gravar"
6. Realize as ações
7. Clique em "Parar"
8. Vídeo salvo em Fotos

---

## Edição do Vídeo

### Software Recomendado

- **Gratuito**:
  - OpenShot (Windows/Linux/macOS)
  - CapCut (Smartphone)
  - DaVinci Resolve (Profissional)

- **Pago**:
  - iMovie (macOS/iOS)
  - Windows Video Editor
  - Adobe Premiere Pro

### Passos Básicos

1. **Importar Vídeo**
   - Abra o software de edição
   - Clique em New Project
   - Importe o arquivo de vídeo

2. **Cortar Partes Desnecessárias**
   - Identifique partes longas/esperando
   - Corte para deixar apenas o essencial

3. **Adicionar Música**
   - Procure música royalty-free em:
     - [Freepik Music](https://www.freepik.com/music)
     - [YouTube Audio Library](https://www.youtube.com/audio_library)
     - [Incompetech](https://incompetech.com/)
   - Adicione ao fundo (volume baixo)

4. **Adicionar Texto/Títulos**
   - Adicione título no início
   - Adicione labels nas ações principais
   - Exemplo: "🗺️ Selecionando Mapa"

5. **Adicionar Efeitos (Opcional)**
   - Transições entre cenas
   - Zoom para destacar áreas
   - Fade in/out

6. **Exportar**
   - Resolução: 1080p (HD)
   - Formato: MP4
   - Codec: H.264

---

## Hospedagem do Vídeo

### Opções

1. **YouTube**
   - Acesse [youtube.com](https://youtube.com)
   - Clique em ícone de câmera → Enviar vídeo
   - Faça upload
   - Privacidade: Unlisted (apenas com link)
   - Copie o link

2. **Loom** (Recomendado para cursos)
   - Acesse [loom.com](https://loom.com)
   - Clique em "Start recording"
   - Escolha "Window"
   - Grave e compartilhe

3. **GitHub Releases**
   - Crie uma Release (veja GITHUB_SETUP.md)
   - Anexe o vídeo ao Release

4. **Google Drive**
   - Upload do arquivo
   - Compartilhe com permissão de view

---

## Exemplo de Transcrição

```
[ABERTURA - 0:00]
"Olá! Vou demonstrar uma aplicação de geolocalização 
que compara três APIs de mapas diferentes."

[GEOLOCALIZAÇÃO - 0:10]
"Primeiro, vamos obter a localização atual do usuário.
Clicando neste botão..."

[RESULTADOS - 0:20]
"A aplicação nos mostra as coordenadas precisas: 
latitude -23.5611, longitude -46.6560"

[BUSCA - 0:30]
"Agora vamos buscar um endereço. Digitando 'Avenida Paulista'..."

[RESULTADOS SEARCH - 0:45]
"Vemos os resultados de acordo com o provedor escolhido.
Vamos alternar entre Google Maps, Mapbox e OpenStreetMap..."

[MAPAS - 1:05]
"Note as diferenças sutis entre cada API em termos 
de cobertura e precisão."

[SALVAR - 1:20]
"Podemos salvar essa localização em nosso banco de dados..."

[LISTA - 1:35]
"E ver todas as nossas localizações salvas aqui."

[ENCERRAMENTO - 1:50]
"Obrigado por assistir! Confira o repositório no GitHub 
para mais detalhes sobre este projeto."
```

---

## Dicas de Apresentação

### ✅ Faça
- Mostre o app rodando suavemente
- Explique cada funcionalidade claramente
- Mostre os resultados de todas as 3 APIs
- Use uma voz clara e bem modulada
- Adicione música de fundo discreta

### ❌ Evite
- Vídeo muito longo (máx. 3 minutos)
- Leitura de código na tela
- Cliques rápidos demais
- Silêncio incômodo
- Mostrar dados sensíveis (chaves, senhas)

---

## Checklist Final

- ✅ Vídeo gravado completamente
- ✅ Áudio claro e de boa qualidade
- ✅ Duração entre 1-3 minutos
- ✅ Todas as funcionalidades demonstradas
- ✅ Texto claro ou narração
- ✅ Editado e sem partes longas
- ✅ Hospedado online
- ✅ Link adicionado ao README
- ✅ Sem exposição de dados sensíveis

---

## Formato Recomendado no GitHub

No seu README:

```markdown
## 🎥 Demonstração em Vídeo

[![Demonstração](https://img.shields.io/badge/Watch-Video-red?style=for-the-badge&logo=youtube)](link-do-video)

[Link do vídeo](link-do-video)

Duração: 2 minutos
```

---

## Recursos Extras

- [Filmora (Editor Gratuito)](https://filmora.wondershare.com/)
- [Adobe Express (Edição Rápida)](https://express.adobe.com/)
- [Claquete Online](https://www.claquete.com/) (Criar thumbnail)

---

Pronto! Com este guia você consegue criar um vídeo profissional em poucos minutos! 🎬