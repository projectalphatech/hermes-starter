# Hermes للمبتدئين: خطوة بخطوة 🤖

[English version](README.en.md)

Hermes agent مجاني و open source من Nous Research. بيكوّد معاك، **بيفتكرك** من يوم للتاني، و**بيعلّم نفسه** skills جديدة، وشغال على **أي موديل** (حتى المجاني).

الريبو ده معمول لو أول مرة تكوّد في حياتك. امشي على الخطوات بالترتيب، ومتنطّش خطوة.

> ⏱️ هتاخد حوالي 15–20 دقيقة.
> مش ريبو رسمي من Nous Research. Hermes نفسه هنا: https://github.com/NousResearch/hermes-agent

---

## قبل ما تبدأ: محتاج إيه؟

- كمبيوتر **Windows 10/11** أو **Mac** أو **Linux**.
- نت كويس (التسطيب بينزّل حاجات).
- مش محتاج تكون عارف برمجة خالص.

---

## الخطوة 0: افتح الـ Terminal

الـ Terminal شاشة سودا بتكتب فيها أوامر للكمبيوتر بدل ما تدوس بالماوس. متخافش منها 😄

**Windows:**
1. دوس على زرار **Start**.
2. اكتب `PowerShell`.
3. افتح **Windows PowerShell**.

**Mac:**
1. دوس `Cmd` + `Space`.
2. اكتب `Terminal` ودوس `Enter`.

**إزاي تلصق أمر جوه الـ Terminal:**
- Windows (PowerShell): انسخ الأمر من هنا، وبعدين **كليك يمين** جوه الشاشة السودا يلصقه. دوس `Enter`.
- Mac: `Cmd` + `V` ثم `Enter`.

---

## الخطوة 1: نزّل Hermes

انسخ الأمر بتاع جهازك بس، والصقه في الـ Terminal، ودوس `Enter`.

**Windows (PowerShell):**

```powershell
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

**Mac أو Linux:**

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```

- التسطيب بينزّل لوحده كل اللي محتاجه (Python و Node.js وغيرهم). سيبه يخلص، ممكن ياخد كام دقيقة.
- لو الـ antivirus اشتكى من ملف اسمه `uv.exe`، ده إنذار غلط معروف. خلّي الـ antivirus يسمح لفولدر Hermes.

**لما يخلص:**
- Windows: **اقفل** PowerShell وافتحه تاني.
- Mac: اكتب `source ~/.zshrc` ودوس `Enter` (أو اقفل الـ Terminal وافتحه تاني).

> 💡 فيه كمان برنامج Desktop بواجهة عادية للـ Windows والـ Mac من موقعهم: https://hermes-agent.nousresearch.com

---

## الخطوة 2: اتأكد إنه اتنزل صح

```bash
hermes doctor
```

لو طلعلك تقرير ومفيش أخطاء حمرا كتير، يبقى تمام ✅
لو طلعلك `'hermes' is not recognized` أو `command not found`، روح على [مشاكل شائعة](#مشاكل-شائعة).

---

## الخطوة 3: اختار المخ (الموديل) 🧠

Hermes نفسه مجرد "جسم". المخ هو الموديل اللي بيفكر. اكتب:

```bash
hermes model
```

وهيسألك تختار provider. عندك 3 طرق **مجانية**، اختار واحدة بس:

### أ) Nous Portal (الأسهل)

```bash
hermes setup --portal
```

بيفتحلك صفحة تسجّل دخول، وبعدها كل حاجة بتتظبط لوحدها. فيه موديلات مجانية (زي LongCat) بحدود استخدام. لو وصلت للحد، Hermes هيقولك إمتى يرجع تاني.

### ب) OpenRouter (موديلات free كتير)

1. ادخل https://openrouter.ai واعمل حساب.
2. من **Keys** دوس **Create Key** وانسخ المفتاح.
3. في `hermes model` اختار **OpenRouter** والصق المفتاح.
4. اختار موديل اسمه آخره `:free`.

### ج) على جهازك من غير نت (Ollama). للأجهزة القوية بس

1. نزّل Ollama من https://ollama.com
2. نزّل موديل من https://ollama.com/library (مثلاً موديل Qwen أو Llama).
3. Hermes محتاج موديل بـ context **64K على الأقل**. شغّل Ollama كده:
   - Mac / Linux: `OLLAMA_CONTEXT_LENGTH=65536 ollama serve`
   - Windows (PowerShell): `$env:OLLAMA_CONTEXT_LENGTH=65536; ollama serve`
4. في `hermes model` اختار **Custom endpoint** واكتب العنوان: `http://127.0.0.1:11434/v1`

> ⚠️ **أي API key زي الباسورد بالظبط.** متبعتهوش لحد، متحطهوش في screenshot، ومترفعهوش على GitHub. Hermes بيحفظه عندك في `~/.hermes/.env`.

---

## الخطوة 4: أول محادثة

```bash
hermes
```

اكتب له:

```text
عرّف نفسك في سطرين، وقولي تقدر تساعدني في إيه
```

لو ردّ عليك، **مبروك، Hermes شغال** 🎉

أوامر مفيدة جوه المحادثة:
- `/new`: محادثة جديدة.
- `/model`: تغيّر الموديل من غير ما تخرج.
- `Ctrl` + `C`: تخرج.

---

## الخطوة 5: أول كود ليك 💻

1. اعمل فولدر لمشروعك وادخله:

```bash
mkdir my-first-site
cd my-first-site
hermes
```

2. انسخ الطلب ده والصقه لـ Hermes (موجود كمان في [examples/first-task.md](examples/first-task.md)):

```text
اعملي صفحة ويب واحدة (index.html) لمطعم كشري اسمه "كشري التحرير":
عنوان كبير، منيو فيها 5 أصناف بالأسعار بالجنيه، زرار "اطلب على واتساب"، وألوان حلوة.
اكتب الملف في الفولدر ده، وقولي أفتحه إزاي.
```

3. هيسألك يكتب الملف، وافق. بعدها افتح `index.html` بالماوس (دبل كليك) وهيفتح في المتصفح.
4. عايز تعدّل؟ قوله بالعربي: "خلّي الألوان أحمر وأصفر" أو "زوّد صور".

---

## الخطوة 6: الذاكرة والـ Skills (اللي بيخلّي Hermes مختلف)

**الذاكرة:** Hermes بيكتب نوتس عنك وعن شغلك، وتاني يوم بيكمّل من مكان ما وقفت. جرّب تقوله:

```text
افتكر إني مبتدئ وبحب الشرح بالمصري وخطوة بخطوة
```

النوتس دي ملفات عادية عندك تقدر تفتحها:
- Mac / Linux: `~/.hermes/memories/MEMORY.md` و `~/.hermes/memories/USER.md`
- Windows: جوه فولدر `%LOCALAPPDATA%\hermes\memories`

**الـ Skills:** لما Hermes يخلص مهمة صعبة، يقدر يحوّلها لـ skill (وصفة مكتوبة)، والمرة الجاية يعملها لوحده وأسرع. موجودة في `~/.hermes/skills/`، وكل skill بتبقى أمر بيبدأ بـ `/` جوه المحادثة.

---

## مشاكل شائعة

| المشكلة | الحل |
|---|---|
| `'hermes' is not recognized` / `command not found` | اقفل الـ Terminal وافتحه تاني. لو لسه، اعمل restart للجهاز. |
| `401` أو `invalid API key` | المفتاح غلط أو اتنسخ ناقص. شغّل `hermes model` تاني والصقه من الأول. |
| `rate limit` على موديل مجاني | استنى شوية، أو غيّر الموديل بـ `/model`. |
| رسالة إن الـ context صغير | الموديل لازم يبقى 64K context على الأقل. اختار موديل أكبر، أو ظبط Ollama زي الخطوة 3-ج. |
| الـ antivirus مسح `uv.exe` | رجّعه وخلّي الـ antivirus يسمح لفولدر Hermes، وبعدين `hermes update`. |
| أي حاجة تانية | `hermes doctor` يقولك فين المشكلة، و `hermes update` يحدّث لآخر نسخة. |

---

## الجاي 👀

في الجزء ٢: إزاي تعمل **فريق agents**، كل واحد بشخصيته والـ skills بتاعته.
تابع [@sharkawyai](https://www.instagram.com/sharkawyai) على Instagram عشان متفوتوش.

---

Hermes Agent © Nous Research، رخصة MIT. الدليل ده من [Project Alpha Tech](https://projectalpha.tech)، رخصة MIT.
