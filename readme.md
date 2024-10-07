# Cookie Clicker Automation Guide

<center><img src="header.jpg"></center>

Este repositório contém um exemplo de automação de navegador utilizando a biblioteca Selenium com Python. O código demonstra como acessar páginas da web, interagir com elementos e realizar cliques em no jogo "Cookie Clicker".

## Pré-requisitos

Certifique-se de que você tenha o Python instalado em sua máquina. Você também precisará instalar as bibliotecas `selenium` e `webdriver_manager`. Você pode fazer isso utilizando o seguinte comando:

```bash
pip install selenium webdriver-manager
```
## Estrutura do Código

O código é dividido em várias células, cada uma responsável por uma parte específica da automação. Aqui está uma explicação detalhada das funções e métodos utilizados.

### Importando Bibliotecas
```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By
```

As bibliotecas acima são importadas para configurar o driver do Chrome e interagir com a página da web.

### Inicializando o WebDriver

```python
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))  # Configura o driver do Chrome
driver.get("https://google.com")  # Acessa o site
print(driver.title)  # Imprime o título da página

```

Nesta parte, inicializamos o driver do Chrome e acessamos a página do Google. O título da página é impresso no console.

### Acessando o Jogo de Clique de Cookies

```python
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))
driver.get("https://orteil.dashnet.org/cookieclicker/")
print(driver.title)

```

Aqui, acessamos o jogo "Cookie Clicker". O título da página é exibido novamente.

### Interagindo com Elementos

#### Selecionando Elementos com `find_element`

```python
button_english = driver.find_element(by=By.ID, value="langSelect-EN")
button_english.screenshot("debug.png")
button_english.click()

```
Neste exemplo, utilizamos o método `find_element` para localizar o botão que altera o idioma para inglês. O botão é clicado, e uma captura de tela é salva.

#### Selecionando Elementos com `find_elements`
```python
def buy_buildings(driver): while True: buildings = driver.find_elements(By.CSS_SELECTOR, ".product.unlocked.enabled") if len(buildings) > 0: buildings[-1].click() else: break
```

Aqui, a função `buy_buildings` utiliza `find_elements` para localizar todos os edifícios disponíveis para compra. Se houver edifícios desbloqueados, o último deles é clicado.

### Comprando Upgrades

```python
def buy_upgrade(driver):
    while True:
        upgrades = driver.find_elements(By.CSS_SELECTOR, ".crate.upgrade.enabled")
        if len(upgrades) > 0:
            upgrades[-1].click()
        else:
            break

```
Esta função é similar à anterior, mas ela busca por upgrades disponíveis e clica no último que encontrar.

### Loop Principal de Cliques

```python
clicks = 0
while True:
    cookie.click()
    clicks += 1
    if clicks % 500 == 0:
        buy_upgrade(driver)
        buy_buildings(driver)

```

No loop principal, o cookie é clicado repetidamente. A cada 500 cliques, as funções `buy_upgrade` e `buy_buildings` são chamadas para comprar upgrades e edifícios.

## Conclusão

Este tutorial demonstrou como usar o Selenium para automatizar um navegador e interagir com elementos de uma página web. Você pode expandir este exemplo para automações mais complexas conforme necessário.

## EsmolaPill
Se você leu até aqui, muito obrigado. Considere adicionar uma ⭐ aqui neste repositório.