# Ether Global Assets - Documentação

Bem-vindo à documentação do aplicativo Ether Global Assets! Este aplicativo permite pagamentos via Pix com criptomoedas e oferece diversas funcionalidades para gerenciamento de ativos.

## Funcionalidades

- Pagamentos via Pix utilizando criptomoedas.
- Suporte a múltiplas redes de blockchain: Ethereum (ETH), Tron (TRX) e Polygon (MATIC).
- Conversão de moedas com taxas e limites definidos.
- Gestão eficiente e segura de ativos digitais.

## Endpoints Principais

### Autenticação

- **Login**: Realiza o login e obtém o token de acesso.
  - **URL**: `{{url}}/auth/login`
  - **Método**: POST
  - **Headers**: 
    - Content-Type: application/json
    - Referer: https://sandbox.etherprivatebank.com.br/
  - **Corpo**:
    ```json
    {
      "email": "{{c_email}}",
      "password": "{{c_password}}"
    }
    ```

### BRCodes

- **Consultar Saldo eBRL**
  - **URL**: `{{url}}/wallets/ebrl-balance`
  - **Método**: GET

- **Criar Pix Dinâmico com Criptomoeda**
  - **URL**: `{{url}}/brcodes/v3/crypto`
  - **Método**: POST
  - **Headers**: 
    - Content-Type: application/json
    - Accept: application/json
  - **Corpo**:
    ```json
    {
      "amount": 1500,
      "network": "ETH",
      "token": "USDTBRL",
      "walletAddress": "0x3cb20c4f4c0b0df25a10e56e0ff5f8619d15dd39"
    }
    ```

- **Pagar Pix com Chave**
  - **URL**: `{{url}}/brcodes/payout/v3/pix-key`
  - **Método**: POST
  - **Headers**:
    - brcodeId: [seu brcodeId aqui]
  - **Corpo**:
    ```json
    {
      "pixKey": "pedrosgmagalhaes@gmail.com",
      "amount": 90,
      "description": "teste teste"
    }
    ```

- **Realizar Pagamento BRCode**
  - **URL**: `{{url}}/brcodes/pay`
  - **Método**: POST
  - **Headers**:
    - Content-Type: application/json
    - Accept: application/json
  - **Corpo**:
    ```json
    {
      "brcode": "[seu brcode aqui]"
    }
    ```

- **Verificar Status**
  - **URL**: `{{url}}/brcodes/v3/status`
  - **Método**: POST
  - **Corpo**:
    ```json
    {
      "brcodeId": "2f075c24075e4e319a9943ec6fe0ed09"
    }
    ```

## Variáveis de Ambiente

- **url**: `https://api.sandbox.etherprivatebank.com.br`
- **c_email**: `admin@etherprivatebank.com.br`
- **c_password**: `newPassword`
- **access_token**: (preencher após login)
