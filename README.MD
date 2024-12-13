# VotAqui

**VotAqui** é um aplicativo de votação desenvolvido com Python e Django,que permite aos usuários criar perguntas e alternativas, submeter votos, armazenar os resultados em um banco de dados, contabilizar os votos e exibir os resultados em formato gráfico.

---

## Funcionalidades

- **Criação de perguntas:** Permite a definição de uma pergunta e suas respectivas alternativas.
- **Submissão de votos:** Usuários podem selecionar uma alternativa e enviar seu voto.
- **Armazenamento de dados:** Todos os votos são armazenados em um banco de dados.
- **Exibição de resultados:** Mostra o número de votos por alternativa e apresenta um gráfico interativo para visualização.
- **Interface responsiva:** Design limpo e responsivo utilizando Bootstrap.

---

## Tecnologias Utilizadas

- **Backend:**
  - Python
  - Django (Framework principal para desenvolvimento do backend e gerência do banco de dados).
- **Frontend:**
  - HTML
  - CSS (com Bootstrap 4)
  - JavaScript (para renderização de gráficos).
- **Banco de Dados:**
  - SQLite (default do Django, mas pode ser facilmente alterado para outros sistemas como PostgreSQL).
- **Gráficos:**
  - Biblioteca ZingChart para criação de gráficos dinâmicos.

---

## Instalando o Projeto

1. Clone este repositório:

   ```bash
   git clone https://github.com/seu-usuario/votaqui.git
   cd votaqui
   ```

2. Crie um ambiente virtual e ative-o:

   ```bash
   python -m venv venv
   source venv/bin/activate # No Windows: venv\Scripts\activate
   ```

3. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

4. Realize as migrações do banco de dados:

   ```bash
   python manage.py migrate
   ```

5. Inicie o servidor de desenvolvimento:

   ```bash
   python manage.py runserver
   ```

6. Acesse o aplicativo no navegador: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

## Utilizando o Aplicativo

1. **Criar uma pergunta:** Acesse o painel de administração do Django (http://127.0.0.1:8000/admin) e crie uma nova pergunta com alternativas.

2. **Submeter votos:** No aplicativo, clique na pergunta para abrir a tela de votação e selecione uma alternativa.

3. **Visualizar resultados:** Após votar, veja os resultados atualizados com o número total de votos e o gráfico dinâmico.

---

## Exemplo de Páginas

### Tela Inicial
- Apresenta uma mensagem de boas-vindas e um link para as votações:

```html
<div class="card text-center">
	<div class="card-body">
		<h1>Bem-vindo ao VotAqui</h1>
		<p>Esse é um exemplo de App de votação em Django</p>
		<a class="btn btn-dark" href="{% url 'polls:index' %}">
			Ver votações disponíveis</a>
	</div>
</div>
```

### Resultados
- Mostra os votos por alternativa e um gráfico interativo:

```html
<ul class="list-group mb-5">
    {% for choice in question.choice_set.all %}
    <li class="list-group-item">
        {{ choice.choice_text }}
        <span class="badge badge-success float-right">
            {{ choice.votes }} voto{{ choice.votes | pluralize }}</span>
    </li>
    {% endfor %}
</ul>
<div id="myChart"></div>
```

### Gráfico Interativo
- O gráfico é renderizado com ZingChart, exibindo votos em tempo real.

```javascript
function buildChart() {
    var chartData = {
        "type": "bar",
        "scale-x": {
            "values": state.items,
            "item": {
                "angle": 270,
                "font-size": "12px",
                "padding-bottom": "10px"
            }
        },
        "series": [
            {
                "values": state.values
            }
        ],
        "plotarea": {
            "margin-bottom": "100px"
        }
    };

    zingchart.render({
        id: "myChart",
        data: chartData,
        width: "100%",
        height: "500px"
    });
}
```

---

## Licença

Este projeto é distribuído sob a licença MIT. Consulte o arquivo LICENSE para obter mais detalhes.

