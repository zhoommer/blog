---
title: 'React, Vue ve Diğer Frontend Kütüphanelerinin Ardındaki Temel Gerçek: Pure HTML, CSS ve JavaScript ile Yapılabilecekler'
description: 'Pure HTML, CSS ve Javascript'
pubDate: 'May 03 2025'
heroImage: '/html_css_js.png'
---

Frontend geliştirme dünyasında, React, Vue, Angular gibi modern kütüphaneler büyük bir popülarite kazandı. Bu kütüphaneler, dinamik ve etkileşimli kullanıcı arayüzleri geliştirmeyi oldukça kolaylaştırıyor. Ancak, bu kütüphanelerin sunduğu avantajların çoğu, aslında modern JavaScript'in ve web tarayıcılarının sunduğu özelliklerle mümkündür. Bu makalede, bu popüler kütüphanelerin sunduğu özelliklerin aslında pure HTML, CSS ve JavaScript ile nasıl yapılabileceğini keşfedeceğiz.

##### Bölüm 1: React ve Vue'un Temel Felsefesi

- React ve Vue, temelde bileşen tabanlı yaklaşımlar sunar. Her bileşen, kendi içinde bağımsızdır ve yalnızca veriye bağlı olarak güncellenir.
- React, "virtual DOM" kullanarak DOM manipülasyonlarını optimize eder. Ancak, aynı şey JavaScript ve DOM API'leri kullanılarak manuel olarak da yapılabilir.
- Vue, reaktif veri bağlama sunarak DOM güncellemelerini otomatikleştirir. Bu tür bir reaktiviteyi manuel olarak JavaScript ile de sağlamak mümkündür.

**Örnek Kod:**
```js
<div id="list"></div>
<button onclick="updateListOptimized()">Optimize Güncelle</button>

<script>
  let currentData = [1, 2, 3];

  // OPTİMİZE: Sadece değişen elemanları günceller ✅
  function updateListOptimized() {
    const newData = [1, 4, 3];
    const list = document.getElementById("list");
    const currentItems = Array.from(list.children);

    // Her elemanı karşılaştır
    newData.forEach((newItem, index) => {
      if (currentItems[index]) {
        // Eleman zaten varsa ve değişmişse güncelle
        if (currentItems[index].textContent !== String(newItem)) {
          currentItems[index].textContent = newItem; // Sadece metni değiştir
        }
      } else {
        // Yeni eleman ekle
        const li = document.createElement("li");
        li.textContent = newItem;
        list.appendChild(li);
      }
    });

    // Fazladan eleman varsa sil
    while (currentItems.length > newData.length) {
      list.removeChild(list.lastChild);
    }
  }

  // İlk yükleme
  updateListOptimized();
</script>
```

##### Bölüm 2: Pure HTML, CSS ve JavaScript ile React ve Vue Özellikleri

**1. Bileşen Yapısı:**
  - Modern JavaScript ile, class yapıları kullanarak bileşenler oluşturabiliriz. render fonksiyonları ve veri bağlamaları, DOM manipülasyonlarıyla taklit edilebilir.

**Örnek Kod:**
```js
<div id="app"></div>

<script>
  // Temel Bileşen Sınıfı (React'ten ilham alınmıştır)
  class Component {
    constructor(props = {}, rootElementId) {
      this.props = props;
      this.state = {};
      this.rootElement = document.getElementById(rootElementId);
    }

    setState(newState) {
      this.state = { ...this.state, ...newState };
      this.#updateDOM(); // State değiştiğinde DOM'u güncelle
    }

    #updateDOM() {
      const newDOM = this.render(); // Yeni DOM'u render et
      this.rootElement.replaceChildren(newDOM); // Sadece değişen kısımları güncelle
    }

    render() {
      throw new Error("render() metodu implemente edilmeli!");
    }
  }

  // Örnek Bileşen: Counter (Sayı Artırma/Azaltma)
  class Counter extends Component {
    constructor(rootElementId) {
      super({}, rootElementId);
      this.state = { count: 0, text: "Merhaba Dünya!" };
    }

    // DOM Oluşturma
    render() {
      const container = document.createElement("div");
      
      // Sayı Görüntüleme
      const countElement = document.createElement("h1");
      countElement.textContent = `Sayı: ${this.state.count}`;

      // Metin Girişi (Two-Way Data Binding)
      const inputElement = document.createElement("input");
      inputElement.value = this.state.text;
      inputElement.addEventListener("input", (e) => {
        this.setState({ text: e.target.value }); // Input değiştiğinde state'i güncelle
      });

      // Düğmeler
      const buttonPlus = document.createElement("button");
      buttonPlus.textContent = "+";
      buttonPlus.addEventListener("click", () => {
        this.setState({ count: this.state.count + 1 }); // State'i güncelle
      });

      const buttonMinus = document.createElement("button");
      buttonMinus.textContent = "-";
      buttonMinus.addEventListener("click", () => {
        this.setState({ count: this.state.count - 1 });
      });

      // Birleştirme
      container.append(
        countElement,
        inputElement,
        document.createElement("br"),
        buttonPlus,
        buttonMinus,
        document.createElement("p").textContent = `Metin: ${this.state.text}`
      );

      return container;
    }
  }

  // Uygulamayı Başlat
  const app = new Counter("app");
  app.#updateDOM(); // İlk render
</script>
```

**2. Veri Bağlama:**

  - React ve Vue'da veri bağlama oldukça yaygın bir tekniktir. Pure JavaScript ile, DOM manipülasyonu ve event listener'lar kullanılarak benzer bir etki oluşturulabilir.

**Örnek Kod:**
```js
<input type="text" id="input">
<p id="output"></p>

<script>
  // Model (Veri Kaynağı)
  const data = {
    _message: "Merhaba",
    get message() {
      return this._message;
    },
    set message(value) {
      this._message = value;
      // Model değiştiğinde DOM'u güncelle
      outputElement.textContent = value; 
      inputElement.value = value; 
    }
  };

  // DOM Elementleri
  const inputElement = document.getElementById("input");
  const outputElement = document.getElementById("output");

  // 1. DOM -> Model Bağlama (Input değiştiğinde)
  inputElement.addEventListener("input", (e) => {
    data.message = e.target.value; // Modeli güncelle
  });

  // 2. Model -> DOM Bağlama (İlk yükleme)
  data.message = data.message; // Tetikleyici
</script>
```

**3. Virtual DOM ve Reaktivite:**

  - Virtual DOM'un temel avantajı, yalnızca değişen kısımların güncellenmesidir. Pure JavaScript ile, DOM değişikliklerini izleyerek benzer bir optimizasyon yapılabilir, ancak kütüphaneler bu süreci oldukça hızlı hale getirir.

##### Bölüm 3: Kütüphanelerin Getirdiği Kolaylıklar ve Avantajlar

- **Hızlı Prototipleme:** React ve Vue, hızlıca kullanıcı arayüzleri geliştirme imkanı sunar. Kütüphaneler, birçok temel işlevselliği hazır olarak sunduğu için, uygulama geliştirme süresi kısalır.

- **Kod Bakımı ve Organizasyonu:** Bileşen tabanlı yaklaşım, özellikle büyük projelerde kodun daha düzenli ve yönetilebilir olmasını sağlar. Pure JavaScript ile bu yapı sağlanabilir, ancak kütüphaneler bu süreci daha sistematik hale getirir.

- **Topluluk Desteği ve Ekosistem:** React ve Vue, büyük topluluklara ve çok sayıda hazır paketlere sahiptir. Bu, geliştiricilerin işini kolaylaştırır ve hızlı çözümler bulmalarına yardımcı olur.

##### Bölüm 4: Sonuç ve Değerlendirme
Modern frontend geliştirme, büyük ölçüde bu kütüphaneler üzerine kuruludur. Ancak, aslında temelde bu kütüphanelerin sunduğu özellikler, pure HTML, CSS ve JavaScript ile yapılabilecek şeylerdir. Kütüphaneler, geliştiricilere kolaylık sağlasa da, temelleri anlamak, bu kütüphaneleri kullanmadan da etkili uygulamalar geliştirebilmek için önemlidir.
