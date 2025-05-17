## 🎮 Unity 2D Game Project Cấu Trúc Thư Mục

```plaintext
📁 Project Unity Game 2D
├── 📄 *.sln
├── 📁 Assets                → Tài nguyên
├── 📁 Library               → Chứa các thư viện liên quan đến xử lý trong Unity (KHÔNG nộp!)
├── 📁 Logs
├── 📁 Packages
│   └── 📄 packages-lock.json → Liệt kê các dependencies trong project
├── 📁 ProjectSettings       → Các cấu hình của project
├── 📁 Temp
└── 📁 UserSettings          → Các cấu hình của tài khoản tạo game (Unity 2D)
```

> 💡 **Khi nộp bài:**
>
> * ❌ Bỏ folder `Library`
> * ✅ Hoặc sử dụng `.gitignore` chuẩn của Unity để loại các thư mục không cần thiết.

---

## 🧩 Cấu Trúc Game Unity

### 1 Game → N Scenes

> 📦 Một game có thể bao gồm nhiều **Scenes** khác nhau đại diện cho từng màn chơi, menu, v.v.

---

### 1 Scene → N GameObjects

> 📌 **Scene** là không gian chứa các thành phần **GameObject** (G.O).

🧠 **Fun fact:** `Camera` cũng là một GameObject — nó có **Transform** riêng như mọi đối tượng khác!

---

### 🖼️ Sprite → GameObject

📥 Khi bạn **kéo một sprite vào Scene**, Unity sẽ tự động biến nó thành **GameObject**!

---

## 🧱 Cấu trúc của GameObject

> 📦 **GameObject = Container của các Component**

### 🔩 Transform `📐`

> 🔧 Mọi GameObject đều bắt buộc có `Transform` — định nghĩa vị trí, xoay và kích thước.

### 🖼️ Sprite Renderer

> 🖼️ Hiển thị hình ảnh sprite 2D gắn vào GameObject.

---

## 🧠 C# Script trong Unity = 1 Component

> ⚙️ Script được gắn như một **Component** vào GameObject → điều khiển hành vi của nó.

### 🧾 Cấu trúc 1 Script

```csharp
public class MyScript : MonoBehaviour {
    // Fields
    // Properties
    // Methods
}
```

> 📦 Mọi script Unity bắt đầu bằng:

```csharp
using UnityEngine;
```

> 💡 Một class script trong Unity thường gồm:
>
> * 🧬 **Fields**
> * 🧱 **Properties**
> * ⚙️ **Methods**

---

## 🔁 MonoBehaviour Class

> 🧠 **MonoBehaviour** là base class cho mọi script Unity.

📚 [🔗 Tài liệu chính thức](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html)

### 🧪 Properties sẵn có

> Gọi trực tiếp trong script:

* `transform`
* `gameObject`
* `tag`
* `enabled`

### 🧰 Public Methods

> 🎯 Unity tự gọi nếu có trong script:

* `Start()`
* `Update()`
* `OnEnable()`, `OnDisable()`
* `OnDestroy()`

### 🌀 Static Methods

> `print("Hello")` → tương tự `Debug.Log()`

### 📩 Event Messages

> ✨ Unity tự trigger đúng lúc:

* `OnCollisionEnter()`
* `OnTriggerEnter()`
* `OnMouseDown()`
* `Update()`, `FixedUpdate()`

> 💬 *Unity sẽ gọi những method này nếu nó tìm thấy trong class!*

### 👨‍👩‍👧 Kế thừa MonoBehaviour

> 🌟 Gíúp bạn sử dụng các thuộc tính và method dựng sẵn như `transform`, `gameObject`, `name`...

---

## ⚠️ TIPS

> ❗ **Khi tạo script mới, KHÔNG đổi tên file ngay sau khi tạo!**
> Class và file script phải trùng tên!

---

### ⚙️ IDE Tích Hợp

📌 **Chọn IDE mặc định:**

1. `Edit → Preferences → External Tools`
2. Chọn `Visual Studio` hoặc `VSCode`

📌 **Cài đặt hỗ trợ Unity:**

* Visual Studio: Chọn Workload `Game development with Unity`
* VS Code: Cài plugin Unity C#

---

## 🎁 Free Assets cho mọi người

> 📦 **Nguồn miễn phí để làm prototype hoặc đồ họa xịn xò**

* [https://www.gameart2d.com/freebies.html](https://www.gameart2d.com/freebies.html)
* [https://gameartpartners.com/downloads/totally-free-goodies/](https://gameartpartners.com/downloads/totally-free-goodies/)
* [https://www.glitchthegame.com/](https://www.glitchthegame.com/)
* [https://www.gamedevmarket.net/](https://www.gamedevmarket.net/)
* [https://opengameart.org/](https://opengameart.org/)
* [https://spritedatabase.net/](https://spritedatabase.net/)
* [https://www.supergameasset.com/](https://www.supergameasset.com/)
* [https://pressstart.vip/tutorials](https://pressstart.vip/tutorials)

---

## 🔄 Game Loop – Ví dụ thực hành

```csharp
using UnityEngine;

public class FirstScript : MonoBehaviour
{
    private float movementSpeed = 5f;

    void Update()
    {
        float horizontalInput = Input.GetAxis("Horizontal");
        float verticalInput = Input.GetAxis("Vertical");

        transform.position = transform.position + new Vector3(horizontalInput * movementSpeed * Time.deltaTime, verticalInput * movementSpeed * Time.deltaTime, 0);

        Debug.Log(transform.position);
    }
}
```

> 📌 `Update()` được gọi mỗi frame → thích hợp xử lý input liên tục!

---

## 📜 Script Lifecycle

```csharp
class Player : MonoBehaviour {
    // Biến public/private
    // Constructor
    void Awake() {}
    void Start() {}
    void Update() {}
    void FixedUpdate() {}
}
```

📘 [Tài liệu Unity về vòng đời script](https://docs.unity3d.com/Manual/ExecutionOrder.html)

---

## 🧱 Lớp quan trọng trong `UnityEngine`

> 📚 **Một số class bạn sẽ dùng rất thường xuyên:**

* `UnityEngine.GameObject`
* `UnityEngine.MonoBehaviour`
* `UnityEngine.Input`
* `UnityEngine.Transform`
* `UnityEngine.Vector3`, `UnityEngine.Vector2`

---

## 🧪 Ví dụ đơn giản

> 🕹️ Di chuyển và xoay nhân vật:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    public float moveSpeed = 5f;
    public Vector3 moveInput;

    void Start() {}

    void Update()
    {
        moveInput.x = Input.GetAxis("Horizontal");
        moveInput.y = Input.GetAxis("Vertical");
        transform.position += moveInput * moveSpeed * Time.deltaTime;

        if (moveInput.x != 0)
        {
            transform.localScale = new Vector3(moveInput.x > 0 ? 1 : -1, 1, 0);
        }
    }
}
```

✅ **Dùng `transform.localScale` để "lật hình" nhân vật khi đi trái/phải.**

---

## 📚 Tài liệu bổ sung

* [📖 Unity Tilemap](https://docs.unity3d.com/Manual/class-Tilemap.html)
* [📖 Unity 2D Overview](https://docs.unity3d.com/Manual/Unity2D.html)
