# 📱 Crypto Monitor - Android App

Aplicativo Android criado com **Kotlin** para acompanhar em tempo real o preço do **Bitcoin**, utilizando requisições HTTP com **Retrofit** e **corrotinas**.

---

## 📁 Estrutura principal do projeto

### 🟢 `MainActivity.kt` (`main`)
Classe principal do app e ponto inicial da aplicação.  
Responsável por:
- Montar a interface da tela inicial  
- Personalizar a barra superior (Toolbar)  
- Controlar o botão **“ATUALIZAR”**  
- Executar a função `makeRestCall()` com uso de **coroutines**

---

### 🟣 `MercadoBitcoinService.kt` (`service`)
Interface responsável por definir os endpoints da API pública do **Mercado Bitcoin**, usando Retrofit.

```kotlin
@GET("api/BTC/ticker/")
suspend fun getTicker(): Response<TickerResponse>
```

---

### 🛠 `MercadoBitcoinServiceFactory.kt` (`service`)
Classe que instancia e configura o Retrofit para uso no projeto.  
Define:
- A base URL: `https://www.mercadobitcoin.net/`  
- O conversor de JSON (GsonConverter)

---

### 🧾 `TickerResponse.kt` (`model`)
Modelo de dados que representa a estrutura da resposta da API.  
Permite acesso aos dados como:
- Último valor da moeda (`last`)
- Data da cotação (`date`)
- Outros valores como `high`, `low`, `vol`, `buy`, `sell`

---

## ▶️ Como executar o projeto

1. Abra o projeto no **Android Studio**
2. Utilize um emulador (recomendado: API 30+) ou conecte um dispositivo físico
3. Clique no botão **Run ▶️**
4. O app será instalado e exibirá a cotação atual do Bitcoin
5. Pressione **“ATUALIZAR”** para buscar os dados mais recentes

---

## ⚙️ Funcionamento do aplicativo

### 1. Inicialização
- Ao abrir o app, a `MainActivity` é iniciada
- A toolbar é configurada com título e cor personalizada
- O botão de atualização é ativado

### 2. Interação do usuário
- Ao tocar no botão, a função `makeRestCall()` é disparada
- A chamada HTTP ocorre sem bloquear a interface do usuário, graças ao uso de `Dispatchers.Main`

### 3. Requisição HTTP
- A chamada é feita para o endpoint `api/BTC/ticker/`
- O Retrofit é configurado dinamicamente via `MercadoBitcoinServiceFactory`

### 4. Apresentação dos dados
- O valor do Bitcoin é exibido em formato monetário BRL (R$), com `NumberFormat`
- A data da cotação é convertida de Unix timestamp para `"dd/MM/yyyy HH:mm:ss"`
- Os dados são exibidos nos componentes `TextView` da interface

### 5. Tratamento de erros
- Em caso de erro HTTP (400, 404 etc), uma mensagem Toast específica é mostrada
- Para falhas inesperadas (sem rede, erro de parsing etc), o app exibe uma mensagem genérica

---

## 📸 Exemplos visuais

### Tela inicial
![Tela inicial](./screenshots/tela_inicial.png)

### Após atualização da cotação
![Cotação atualizada](./screenshots/atualizado.png)

> 📝 *As imagens devem ser salvas na pasta `screenshots/` do repositório.*

---

## 📌 Tecnologias utilizadas

- Kotlin
- Retrofit
- Coroutines
- AndroidX
- Material Design

---

## 💡 Possíveis melhorias futuras

- Adicionar suporte a outras criptomoedas além do Bitcoin  
- Exibir gráfico com histórico de preços  
- Notificações em tempo real para mudanças bruscas de valor  
- Dark mode automático baseado no sistema

---

**Feito com 💻 por [Seu Nome]**
