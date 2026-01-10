# Markdown Syntax Guide (Markdown Kaise Likhein)

Yah guide aapko sikhayegi ki GitHub par Markdown (`.md`) file mein formatting kaise karein.

## 1. Headings (Heading Kaise Banayein)
Heading ke liye `#` ka use karein.
# H1 - Sabse Badi Heading
## H2 - Medium Heading
### H3 - Choti Heading

---

## 2. Text Formatting (Text Style)
* **Bold:** Text ko `**` ke beech mein likhein. Example: **Bold Text**
* *Italic:* Text ko `*` ke beech mein likhein. Example: *Italic Text*
* ~~Strikethrough:~~ Text ko `~~` ke beech mein likhein.

---

## 3. Lists (List Banana)

**Bullet List:**
- Item 1
- Item 2
  - Sub Item (Tab dabayein)

**Numbered List:**
1. Step One
2. Step Two

---

## 4. Inserting Images (Photo Kaise Lagayein)
Photo lagane ke liye syntax: `![Alt Text](Image_URL)`

**Example:**
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

> **Tip:** Agar photo computer mein hai, to GitHub editor mein photo ko "Drag and Drop" karein, link apne aap ban jayega.

---

## 5. Links (Link Lagana)
[Google Par Jayein](https://www.google.com)
Syntax: `[Link Ka Naam](URL)`

---

## 6. Creating Tables (Table Kaise Banayein)
Table banane ke liye `|` aur `-` ka use hota hai.

| Serial No. | Name       | Role          |
| :---       | :---:      | ---:          |
| 1          | Amit       | Developer     |
| 2          | Rahul      | Designer      |
| 3          | Sneha      | Manager       |

*Explanation:*
* `:---` = Left Align
* `:---:` = Center Align
* `---:` = Right Align

---

## 7. Code Blocks (Code Dikhana)
Agar aapko code likhna hai to 3 backticks (```) use karein:

```python
print("Hello World")



```

## Advanced Table Example (Notes ke liye)

Yahan ek example hai ki badi information ko Table mein kaise sajayein (Jaise *Primary* vs *Standby* ya *Topic* vs *Details*).

| Topic | Details & Process |
| :--- | :--- |
| **1. Google SEO Settings** | **Zaroori Settings:**<br>1. **Public Repo:** Repository "Public" honi chahiye.<br>2. **About Section:** Right side mein description likhein.<br>3. **Tags:** `markdown`, `oracle`, `guide` jaise tags lagayein. |
| **2. Image Uploading** | **Asaan Tarika:**<br>1. Apne computer se photo ko **Drag** karein.<br>2. GitHub ke text box mein **Drop (Chhod)** dein.<br>3. GitHub khud uska link bana dega. |
| **3. Future Plan** | Yeh table mujhe yaad dilayegi ki:<br>- Table mein `Enter` nahi, `<br>` use karna hai.<br>- Heading (`###`) nahi, **Bold** use karna hai. |
## 5. Table with Images (Table mein Photo Kaise Lagayein)

Yeh example dikhata hai ki table ke andar chhotte icons ya screenshots kaise set karein.

| Status Type | Icon/Image | Description |
| :--- | :---: | :--- |
| **Success** | ![Check](https://img.icons8.com/emoji/48/000000/check-mark-button.png) | Jab backup complete ho jaye. |
| **Warning** | ![Warning](https://img.icons8.com/emoji/48/000000/warning-emoji.png) | Jab disk space low ho. |
| **Error** | ![Error](https://img.icons8.com/emoji/48/000000/cross-mark-emoji.png) | Jab database down ho. |
| **Screenshot** | ![My Photo](my-photo.jpg) | (Yahan aap apni upload ki hui photo ka naam likhein) |
