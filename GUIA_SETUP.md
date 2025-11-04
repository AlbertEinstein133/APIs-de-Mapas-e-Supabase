# Guia Completo de Setup

## Passo 1: Preparação do Ambiente

### 1.1 Instalar Node.js

Baixe e instale Node.js 18+ de [nodejs.org](https://nodejs.org/)

Verifique a instalação:
```bash
node --version
npm --version
```

### 1.2 Clonar ou Criar o Repositório

```bash
# Se clonando
git clone <seu-repositorio>
cd geolocation-app

# Se criando do zero
npx create-expo-app geolocation-app
cd geolocation-app
```

---

## Passo 2: Instalar Dependências

```bash
npm install expo-location @supabase/supabase-js axios
```

ou se preferir com yarn:

```bash
yarn add expo-location @supabase/supabase-js axios
```

---

## Passo 3: Configurar Supabase

### 3.1 Criar Conta no Supabase

1. Acesse [supabase.com](https://supabase.com)
2. Clique em "Start your project"
3. Entre com GitHub ou email
4. Crie um novo projeto

### 3.2 Obter Credenciais

Após criar o projeto:

1. Vá para **Settings** → **API**
2. Copie:
   - `Project URL` → `EXPO_PUBLIC_SUPABASE_URL`
   - `anon public` key → `EXPO_PUBLIC_SUPABASE_ANON_KEY`

### 3.3 Criar Tabela de Localizações

No Supabase, vá para **SQL Editor** e execute:

```sql
-- Criar tabela
CREATE TABLE locations (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  nome TEXT NOT NULL,
  latitude FLOAT NOT NULL,
  longitude FLOAT NOT NULL,
  endereco TEXT,
  timestamp TIMESTAMP NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Criar índices
CREATE INDEX idx_locations_created_at ON locations(created_at DESC);
CREATE INDEX idx_locations_coords ON locations(latitude, longitude);

-- Habilitar RLS
ALTER TABLE locations ENABLE ROW LEVEL SECURITY;

-- Políticas de acesso
CREATE POLICY "Enable read access" ON locations
  FOR SELECT USING (true);

CREATE POLICY "Enable insert access" ON locations
  FOR INSERT WITH CHECK (true);

CREATE POLICY "Enable delete access" ON locations
  FOR DELETE USING (true);

CREATE POLICY "Enable update access" ON locations
  FOR UPDATE USING (true);
```

### 3.4 Verificar Tabela

Vá para **Table Editor** e verifique se a tabela `locations` foi criada com sucesso.

---

## Passo 4: Configurar APIs de Mapas (Opcional)

### 4.1 Google Maps API

#### Setup:

1. Acesse [Google Cloud Console](https://console.cloud.google.com/)
2. Crie um novo projeto
3. Ative as APIs:
   - Maps JavaScript API
   - Geocoding API
   - Static Maps API
4. Crie uma chave de API em **Credenciais**
5. Restrinja a chave a Android e iOS (opcional)

#### No Arquivo .env:

```env
EXPO_PUBLIC_GOOGLE_MAPS_API_KEY=AIza...SuA
```

#### Restrição de Chave (Recomendado):

Na Google Cloud Console:
- Vá para **Credenciais**
- Clique em sua chave de API
- Em "API restrictions", selecione apenas as APIs acima
- Em "Application restrictions", selecione:
  - Android app: com.seu.app
  - iOS app: com.seu.app

### 4.2 Mapbox

#### Setup:

1. Acesse [mapbox.com](https://www.mapbox.com/)
2. Crie conta ou faça login
3. Vá para **Account** → **Tokens**
4. Crie um novo token (public scope)
5. Copie o token

#### No Arquivo .env:

```env
EXPO_PUBLIC_MAPBOX_ACCESS_TOKEN=pk.eyJ...
```

### 4.3 OpenStreetMap

Nenhuma configuração necessária! 🎉

---

## Passo 5: Criar Arquivo .env

Na raiz do projeto:

```bash
touch .env
```

Conteúdo do `.env`:

```env
# Supabase (OBRIGATÓRIO)
EXPO_PUBLIC_SUPABASE_URL=https://seu-projeto.supabase.co
EXPO_PUBLIC_SUPABASE_ANON_KEY=eyJhbGc...

# Google Maps (Opcional)
EXPO_PUBLIC_GOOGLE_MAPS_API_KEY=AIza...

# Mapbox (Opcional)
EXPO_PUBLIC_MAPBOX_ACCESS_TOKEN=pk.eyJ...
```

---

## Passo 6: Executar a Aplicação

### 6.1 Modo Desenvolvimento

```bash
npm start
```

Você verá um menu com opções:

```
>  Monitor app in development
   Expo Go - scan to open in Expo Go
   Android Emulator
   iOS Simulator
   Web
```

### 6.2 No Simulador/Emulador

#### iOS:
```bash
npm run ios
```

Pré-requisitos:
- macOS
- Xcode instalado
- Simulator

#### Android:
```bash
npm run android
```

Pré-requisitos:
- Android Studio instalado
- Emulator configurado
- ANDROID_HOME setado

### 6.3 Na Web:
```bash
npm run web
```

Nota: Geolocalização é limitada na web

---

## Passo 7: Testar a Aplicação

### 7.1 Testar Geolocalização

1. Abra o app no simulador/emulador
2. Clique em "📍 Obter Localização Atual"
3. Conceda permissão quando solicitado
4. Verifique se as coordenadas aparecem

### 7.2 Testar Geocodificação

1. Busque por um endereço: "Avenida Paulista, São Paulo"
2. Selecione um resultado
3. Veja as coordenadas aparecerem

### 7.3 Testar Supabase

1. Selecione uma localização
2. Clique em "💾 Salvar Localização"
3. Verifique se aparece na lista
4. Vá ao Supabase e confirme na tabela `locations`

### 7.4 Testar APIs Diferentes

1. Mude entre "Google Maps", "Mapbox" e "OpenStreetMap"
2. Busque o mesmo endereço em cada API
3. Observe as diferenças de resultados

---

## Passo 8: Build para Publicação (Opcional)

### 8.1 Build para iOS

```bash
eas build --platform ios
```

Pré-requisitos:
- Conta Expo
- Apple Developer Account
- Certificados de desenvolvimento

### 8.2 Build para Android

```bash
eas build --platform android
```

Pré-requisitos:
- Conta Expo
- Google Play Developer Account
- Keystore configurado

---

## Troubleshooting

### ❌ Erro: "SUPABASE_URL is not set"

**Solução**: 
- Verifique se `.env` existe e tem as variáveis
- Reinicie o servidor: `npm start`

### ❌ Erro: "Permission denied for geolocation"

**Solução**:
- iOS: Vá a Settings → Seu App → Location → Allow
- Android: Vá a Settings → Apps → Seu App → Permissions → Location

### ❌ Erro: "API key not valid"

**Solução**:
- Verifique se a chave está correta em `.env`
- Confirmou a chave em Google Cloud Console?
- Habilitou a API?

### ❌ Erro: "Network request failed"

**Solução**:
- Verifique conexão de internet
- Tente novamente
- Verifique limites de requisições das APIs

### ❌ Erro: "Cannot find module '@supabase/supabase-js'"

**Solução**:
```bash
npm install @supabase/supabase-js
npm start
```

---

## Dicas de Desenvolvimento

### Hot Reload

A aplicação recarrega automaticamente quando você salva mudanças. Pressione:
- **iOS Simulator**: `Cmd + R`
- **Android Emulator**: `Cmd + R` ou `R R`
- **Web**: Recarrega automaticamente

### Debug

Pressione:
- **iOS/Android**: `Cmd + D` (macOS) ou `Ctrl + D` (Windows/Linux)
- Abra o menu de debug

### Console Logs

Ver logs no terminal onde rodou `npm start`

---

## Próximos Passos

1. ✅ Setup completo
2. Explorar funcionalidades
3. Customizar design
4. Adicionar mais features
5. Build e publicar

---

## Recursos Úteis

- [Expo Documentation](https://docs.expo.dev/)
- [React Native Documentation](https://reactnative.dev/)
- [Supabase Documentation](https://supabase.com/docs)
- [Expo Location](https://docs.expo.dev/versions/latest/sdk/location/)
- [Community Forum](https://forums.expo.dev/)

---

## Suporte

Se encontrar problemas:

1. Verifique este guia novamente
2. Procure na [documentação oficial](https://docs.expo.dev/)
3. Pesquise no [Stack Overflow](https://stackoverflow.com/questions/tagged/expo)
4. Pergunte na [comunidade Expo](https://forums.expo.dev/)

Boa sorte! 🚀