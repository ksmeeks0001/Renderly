# Renderly

**Renderly** is a minimalistic Python web framework built around [Mako templates](https://www.makotemplates.org/). With Renderly, all you need to do is drop `.template` files in a directory — and your app is live. It’s perfect for small apps, prototypes, and template-driven workflows.

---

## 🚀 Features

- 🧾 Automatic route-to-template mapping  
- 💡 Clean, Mako-based templating with inheritance and Python expressions  
- 🔁 Request and response objects available in templates  
- 🔧 Custom application context injection  
- 📄 Built-in 404 template support  

---

## 🛠️ Usage


### Example Template (`index.template`)

```mako
<%! from datetime import datetime %>
<h1>${APP_NAME}</h1>
<p>Current time: ${datetime.now()}</p>
<p>Request method: ${request.method}</p>
```

```bash
pip install renderly
```

In `run.py`:

```python
from renderly import App

application = App(name="Renderly Demo", project_dir="templates")
```
## Run with uwsgi

```bash
uwsgi --http :8000 --wsgi-file run.py --callable application
```


---

## 📦 App Context

You can pass global values into templates via `app_context`:

```python
App(name="Renderly", app_context={"version": "1.0"})
```

Then use `${version}` in your templates.

---

## ⚠️ 404 Handling

If a requested template doesn’t exist, Renderly will render the fallback file (default: `404.template`).

---
See the example folder for more usage.

