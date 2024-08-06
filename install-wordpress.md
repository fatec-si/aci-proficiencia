# Instalação Wordpress

1. Instale o Wordpress via [wordpress.org](https://wordpress.org/download/).

2. Instale o tema `Zakra`.

```
wp-admin/theme-install.php?search=zakra
```

3. Instale o template `Ladies Shop`.

```
wp-admin/themes.php?page=zakra&tab=starter-templates
```

4. Instale e ative o plugin `Pix Automático com Pagarme para WooCommerce`:

```
wp-admin/plugin-install.php?s=Pix%2520Autom%25C3%25A1tico%2520com%2520Pagarme%2520para%2520WooCommerce%2520&tab=search&type=term
```

5. Instale e ative o plugin `WooCommerce Boleto e PIX PagHiper`:`

```
wp-admin/plugin-install.php?s=WooCommerce%2520Boleto%2520e%2520PIX%2520PagHiper&tab=search&type=term
```

6. Confira se os dois estão ativos:

```
wp-admin/plugins.php
```

7. Ative todas as formas de pagamento, menos a `paghiper_PIX`:

```
wp-admin/admin.php?page=wc-settings&tab=checkout
```

8. Configure a transferencia bancaria com dados de placeholder:

```
wp-admin/admin.php?page=wc-settings&tab=checkout&section=bacs
```

9. Coloque qualquer coisa na `API key` e `Token PagHiper` (configuração do `paghiper_boleto`):

```
wp-admin/admin.php?page=wc-settings&tab=checkout&section=paghiper_billet 
```

10. Coloque qualquer coisa na `Pagar.me API Key` e `Pagar.me Encryption Key` (configuração do PIX do Pagar.me):

```
wp-admin/admin.php?page=wc-settings&tab=checkout&section=paghiper_pix
```

11. Edite o arquivo `PagarmeApiV4.php`, dentro de `wp-content\plugins\wc-pagarme-pix-payment\src\Pagarme\PagarmeApiV4.php`.
    
  - Comente da linha 58 até a 61;
  - Comente a linha 125;
  - Coloque o código abaixo na linha 126:

```php
  $transaction = array(
    'pix_qr_code'=>"123",
    'id'=>123,
    'status'=>"pending"
  );
```

12. Edite o arquivo `class-wc-paghiper-transaction.php`, dentro de `wp-content\plugins\woo-boleto-paghiper\includes\class-wc-paghiper-transaction.php`.
    
  - Comente da linha 436;
  - Coloque o código abaixo na linha 437:

```php
$response = array(
  'transaction_id' => '123456',
  'value_cents' => 10000,
  'status' => 'pending',
  'order_id' => 'order_7890',
  'due_date' => '2024-12-31',
  'bank_slip' => array(
    'digitable_line' => '34191.79001 01043.510047 91020.150008 5 12340000001000',
    'url_slip' => 'https://example.com/slip',
    'url_slip_pdf' => 'https://example.com/slip.pdf',
    'bar_code_number_to_image' => '34191790010104351004791020150008512340000001000',
  ),
);
```
