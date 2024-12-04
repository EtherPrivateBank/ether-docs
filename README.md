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
  - **URL**: `https://api.sandbox.etherglobalassets.com.br/auth/login`
  - **Método**: POST
  - **Headers**: 
    - Content-Type: application/json
    - Referer: https://sandbox.etherglobalassets.com.br/
  - **Corpo**:
    ```json
    {
      "email": "{{c_email}}",
      "password": "{{c_password}}"
    }
    ```

### BRCodes

- **Consultar Saldo eBRL**
  - **URL**: `https://api.sandbox.etherglobalassets.com.br/wallets/ebrl-balance`
  - **Método**: GET

- **Criar Pix Dinâmico com Criptomoeda**
  - **URL**: `https://api.sandbox.etherglobalassets.com.br/brcodes/v3/crypto`
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
  - **URL**: `https://api.sandbox.etherglobalassets.com.br/brcodes/payout/v3/pix-key`
  - **Método**: POST
  - **Headers**:
    - brcodeId: [seu brcodeId aqui]
  - **Corpo**:
    ```json
    {
      "pixKey": "exemplo@dominio.com",
      "amount": 90,
      "description": "teste teste"
    }
    ```

- **Realizar Pagamento BRCode**
  - **URL**: `https://api.sandbox.etherglobalassets.com.br/brcodes/pay`
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
  - **URL**: `https://api.sandbox.etherglobalassets.com.br/brcodes/v3/status`
  - **Método**: POST
  - **Corpo**:
    ```json
    {
      "brcodeId": "2f075c24075e4e319a9943ec6fe0ed09"
    }
    ```

## Variáveis de Ambiente

- **url**: `https://api.sandbox.etherglobalassets.com.br`
- **c_email**: `admin@exemplo.com`
- **c_password**: `senhaFicticia123`
- **access_token**: (preencher após login)
