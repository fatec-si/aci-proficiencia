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
