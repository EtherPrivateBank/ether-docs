# Documento: Endpoint de Criação de Pix Dinâmico para USDT

Este documento descreve o funcionamento do endpoint para a criação de um Pix dinâmico, que permite a realização de pagamentos via Pix utilizando criptomoedas.

## Endpoint

**URL:** `POST {{host}}/brcodes/v3/crypto`

### Corpo da Requisição

A requisição deve ser enviada no formato JSON, contendo os seguintes campos:

```json
{
    "amount": 1500,
    "network": "ETH",
    "token": "USDTBRL",
    "walletAddress": "0x3cb20c4f4c0b0df25a10e56e0ff5f8619d15dd39"
}
```

- **amount**: Valor em reais a ser convertido para criptomoeda.
- **network**: Rede de blockchain a ser utilizada. As opções disponíveis são `ETH` (Ethereum), `TRX` (Tron) e `MATIC` (Polygon).
- **token**: Token a ser utilizado na transação. Exemplo: `USDTBRL`.
- **walletAddress**: Endereço da carteira de destino.

### Resposta

A resposta é retornada em formato JSON, contendo as seguintes informações:

```json
{
    "message": "Dynamic Brcode created successfully using v3",
    "data": {
        "uuid": "766b846ceb2b4e08ab622ec88f292b12",
        "brcodeId": "00020101021226790014br.gov.bcb.pix2557brcode.starkinfra.com/v2/766b846ceb2b4e08ab622ec88f292b125204000053039865802BR5925Bsb Instituicao de Pagame6008Contagem62070503***63048F04",
        "tags": [
            "d13cb1c4907e47b"
        ],
        "pictureUrl": "https://api.starkbank.com/v2/dynamic-brcode/766b846ceb2b4e08ab622ec88f292b12.png",
        "prchaseFlowId": "674cdbda7772188f5ff6209f",
        "amount": 1500,
        "tradePrice": "6.156",
        "totalAmountPreview": "2.44",
        "fees": 72,
        "created": "2024-12-01T21:57:46.321Z",
        "updated": "2024-12-01T21:57:46.321Z"
    }
}
```

- **message**: Mensagem de confirmação da criação do Pix.
- **uuid**: Identificador único do Pix gerado.
- **brcodeId**: Identificador do Pix para pagamento via Pix.
- **tags**: Tags associadas à transação.
- **pictureUrl**: URL da imagem do Pix gerado.
- **prchaseFlowId**: Identificador do fluxo de compra.
- **amount**: Valor original da transação em reais.
- **tradePrice**: Preço de conversão da criptomoeda.
- **totalAmountPreview**: Valor total em criptomoeda após a conversão.
- **fees**: Taxas aplicadas na transação.
- **created**: Data e hora de criação.
- **updated**: Data e hora da última atualização.

## Detalhes do Funcionamento

- **Pagamento via Pix**: O usuário pode realizar o pagamento utilizando o `brcodeId` ou a imagem gerada no `pictureUrl`.
- **Taxas**: O valor de `fees` é gerado com um custo fixo de 64 centavos para o cash in do Pix.
- **Conversão de Moeda**: Na conversão de reais para PIX, há um spread de 2,5% referente à compra de USDT em reais.
- **Redes Suportadas**: As redes suportadas são `ETH`, `TRX` (Tron) e `Polygon`, devendo ser especificadas na requisição.

Este endpoint oferece uma forma eficiente e segura de realizar pagamentos via Pix utilizando criptomoedas, com suporte a múltiplas redes de blockchain.