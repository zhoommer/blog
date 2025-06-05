---
title: 'Hazır UI Kütüphanelerinden Vazgeçip Saf HTML/CSS’e Dönmek'
description: 'HTML/CSS'
pubDate: 'Jun 5 2025'
heroImage: '/pure_css.png'
---


## Giriş

Modern frontend geliştirmede hız ve tutarlılık sağlamak amacıyla Tailwind CSS ve shadcn/ui gibi hazır kütüphaneler sıkça tercih ediliyor. Bu yazıda, yakın zamanda üzerinde çalıştığım bir projede yaşadığım UI bileşeni hatasını (örneğin user menu bileşeninin bir anda çalışmamaya başlaması) ele alacağım. Ardından, neden saf HTML ve CSS ile kendi UI’ınızı geliştirmenin hâlâ güçlü bir seçenek olduğuna dair çıkarımlarımı paylaşacağım.

## Proje ve Kullanılan Teknolojiler

* **Tailwind CSS:** Utility-first yaklaşımıyla stil vermeyi kolaylaştırıyor.
* **shadcn/ui:** Tailwind üzerine inşa edilmiş, önceden tasarlanmış React bileşen kütüphanesi.

Bu kombinasyon, başlangıçta hızlı prototipleme ve tutarlılık vaadi sunuyor olsa da, bazı durumlarda beklenmedik davranışlar ve bağımlılık sorunlarıyla karşılaşabiliyor.

## Yaşadığım Sorun

1. **User Menu Bileşeni:** Profil fotoğrafına tıklandığında açılması gereken dropdown menüsü, aniden tepki vermemeye başladı.
2. **Debug Süreci:**
   * Versiyon kontrolünde geri alıp farklı Tailwind ve shadcn versiyonlarını denedim.
   * Bileşen kodunu sadeleştirip minimal bir test ortamında çalıştırdım.
   * Chrome DevTools’tan event listener ve CSS çakışmalarını inceledim.
3. **className Karmaşası:** Tailwind'in utility-first yaklaşımı nedeniyle HTML elementlerinin className'leri çok uzun ve karmaşık hale geldi. Hangi stilin nereden geldiğini takip etmek zorlaştı.
  * Tailwind örneği: 
  ```html
  <div class="flex items-center justify-between px-4 py-2 bg-white border border-gray-300 rounded-lg shadow-md hover:bg-gray-100 transition duration-300 ease-in-out text-sm text-gray-800 font-medium">
  Card
  </div>
```
  * Css Örneği:
  ```css
.card {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 1rem;
  background-color: white;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  font-size: 0.875rem;
  font-weight: 500;
  color: #1f2937;
  transition: background-color 0.3s ease-in-out;
}
.card:hover {
  background-color: #f3f4f6;
}
```
* Şimdi div elementimi bu şekilde kullanabilirim. 
```html
<div class='card'>Card</div>
```

4. **Sonuç:** Her denemede farklı bir hata veya sıfır tepki; sonuçta bileşeni eski haline döndürmek için çok fazla zaman harcadım.

## Çözüm Arayışları

* **Kütüphane Güncellemeleri:** Sürüm uyumsuzluklarını gidermek adına Tailwind ve shadcn’u güncelledim.
* **Kod Sorgulaması:** Tipografi, spacing, z-index ve event handler konfigürasyonlarını yeniden ele aldım.
* **Topluluk Kaynakları:** GitHub Issues ve Discord kanallarında benzer problem yaşayanların çözümlerini aradım.

Ancak nihayetinde, bu süreç projenin hızını ve verimliliğini olumsuz etkiledi.

## Saf HTML ve CSS ile Kendi UI’ınızı Oluşturmak

### Avantajlar

* **Bağımlılıktan Kurtulma:** Ekstra paket yüklemeye gerek kalmadan sade ve anlaşılır yapı.
* **Kontrol:** Her detayın sizde olması, beklenmedik çakışmaların önüne geçer.
* **Performans:** Gereksiz CSS yükü ortadan kalkar.

### Örnek: Basit Dropdown Menü

```html
<div class="dropdown">
  <button id="menuToggle">Profil</button>
  <ul id="menuList" class="hidden">
    <li><a href="/profile">Profilim</a></li>
    <li><a href="/settings">Ayarlar</a></li>
    <li><a href="/logout">Çıkış</a></li>
  </ul>
</div>
```

```css
.dropdown { position: relative; display: inline-block; }
#menuList {
  position: absolute; top: 100%; left: 0;
  list-style: none; margin: 0; padding: 0;
  border: 1px solid #ccc; background: #fff;
}
.hidden { display: none; }
```

```js
const toggle = document.getElementById('menuToggle');
const list = document.getElementById('menuList');
toggle.addEventListener('click', () => {
  list.classList.toggle('hidden');
});
```

Bu yaklaşım, öğrenmesi ve sürdürmesi son derece basit, ayrıca tamamen projenize özgü tasarımlar yapmanızı sağlıyor.

## Sonuç ve Öneriler

* Hazır kütüphaneler hız kazandırsa da, karmaşık bağımlılıklar bazen maliyeti artırabilir.
* Küçük veya orta ölçekli projelerde, saf HTML/CSS/JavaScript ile bileşenlerinizi inşa etmek daha sürdürülebilir ve özelleştirilebilir olabilir.
* UI ihtiyaçlarınız yoğun değilse, gereksiz yükten kaçınmak için kendi basit çözümlerinize yönelebilirsiniz.

Kütüphane kullanım kararınızı verirken, projenizin kapsamı ve uzun vadeli bakım maliyetini göz önünde bulundurun.

