---
title: 'Neovim Neden Günlük Kullandığım Editör Haline Geldi'
description: 'Neovim'
pubDate: 'May 02 2025'
heroImage: '/lazyvim.png'
---

Geliştiriciler arasında metin editörü seçimi bir tartışma konusu olmaktan ziyade, bir öz kimlik beyanı haline geldi. Kimileri Visual Studio Code’un eklenti zenginliğine, kimileri ise JetBrains IDE’lerinin kapsamlı özelliklerine bağlı kalırken, ben Neovim’i tercih ettim. Bu makalede, Neovim’i neden benimsediğimi ve günlük çalışma akışımda bana nasıl fayda sağladığını anlatacağım.

##### Minimalizm ve Hızlı Performans
[Neovim](https://neovim.io/), minimal bir yapı sunar. Modern metin editörlerinde bulunan çok sayıdaki görsel arayüz elementleri yerine, saf ve etkili bir metin işleme deneyimi sağlar. Bunun bir sonucu olarak, Neovim hem çok daha hızlı çalışır hem de kaynak kullanımı açısından hafiftir. Bilgisayarınızın kaynaklarını zorlamadan etkili bir şekilde kod yazabilirsiniz.

##### Özelleştirilebilirlik
Bir diğer büyük avantajı, Neovim’in tamamen özelleştirilebilir bir yapıya sahip olmasıdır. Kendi ihtiyaçlarınıza göre anahtar atamaları, renk temaları ve eklentilerle çalışma ortamınızı şekillendirebilirsiniz. LazyVim gibi önceden ayarlanabilir eklenti paketlerini kullanarak zamandan tasarruf edebilirsiniz.

##### LazyVim ile Verimlilik
[LazyVim](https://www.lazyvim.org/), Neovim’in özelleştirilebilirliğini öne çıkaran harika bir aracıdır. LazyVim sayesinde Neovim’i kurmak ve kullanmak çok daha kolay bir hale geliyor. Özellikle karmaşık yapılandırma süreçlerinden kaçınmak isteyen geliştiriciler için bu büyük bir avantaj.

##### Fzf ile Hızlı Arama
Neovim, [Fzf](https://github.com/junegunn/fzf) (“Fuzzy Finder”) gibi eklentilerle dosya ve metin aramalarını çok daha hızlı hale getirebilir. Bu, özellikle büyük projelerde zaman kazandırır ve aradığınız içeriğe anında ulaşmanızı sağlar.

##### Kısayol Tuşları ile Verimlilik
Neovim’in klavye kısayolları, kodlama sürecini çok daha akıcı hale getiriyor.
İşte bazı örnekler:

##### 🧭 Navigasyon
```markdown
| Tuş                 | Eylem                                                            |
| ------------------- | ---------------------------------------------------------------- |
| `h`, `j`, `k`, `l`  | Sola, aşağı, yukarı, sağa hareket et                             |
| `w` / `W`           | Kelime bazında ileri git (W: boşlukla ayrılmış kelimeler)        |
| `b` / `B`           | Kelime bazında geri git                                          |
| `0` / `^` / `$`     | Satırın başına / boşluk olmayan ilk karaktere / satır sonuna git |
| `gg` / `G`          | Dosyanın başına / sonuna git                                     |
| `Ctrl-d` / `Ctrl-u` | Sayfanın yarısı kadar aşağı / yukarı kaydır                      |
| `%`                 | Eşleşen paranteze veya süslü paranteze atla                      |
```

##### ✏️  Düzenleme
```markdown
| Tuş       | Eylem                                      |
| --------- | ------------------------------------------ |
| `i` / `I` | Ekleme moduna geç / Satır başında ekleme   |
| `a` / `A` | İmleçten sonra ekle / Satır sonunda ekle   |
| `o` / `O` | Alt satıra / Üst satıra yeni satır aç      |
| `x` / `X` | İmleç altındaki / önceki karakteri sil     |
| `dd`      | Mevcut satırı sil (kes)                    |
| `yy`      | Mevcut satırı kopyala                      |
| `p` / `P` | Kopyalananı imleçten sonra / önce yapıştır |
| `u`       | Son işlemi geri al                         |
| `Ctrl-r`  | Geri alınanı tekrar yap                    |
```

##### 🔍 Arama ve Değiştirme
```markdown
| Tuş                 | Eylem                                                       |
| ------------------- | ----------------------------------------------------------- |
| `/kelime`           | İleriye doğru kelime ara                                    |
| `?kelime`           | Geriye doğru kelime ara                                     |
| `n` / `N`           | Aramayı aynı yönde / ters yönde tekrar et                   |
| `:%s/eskisi/yeni/g` | Dosya içindeki tüm `eskisi` ifadelerini `yeni` ile değiştir |
| `:noh`              | Arama vurgusunu temizle                                     |
```
##### 🎯 Faydalı Komutlar
```markdown
| Komut                 | Eylem                                        |
| --------------------- | -------------------------------------------- |
| `:e dosya_adi`        | Bir dosya aç                                 |
| `:w` / `:q` / `:wq`   | Kaydet / çık / kaydet ve çık                 |
| `:vsp dosya_adi`      | Dikey bölme ile dosya aç                     |
| `:sp dosya_adi`       | Yatay bölme ile dosya aç                     |
| `Ctrl-w h/j/k/l`      | Bölmeler arasında sola/aşağı/↑/sağa geçiş    |
| `:buffers` / `:bnext` | Açık tamponları göster / sonraki tampona geç |
```

##### 🔁 Makro
```markdown
| Tuş  | Eylem                                    |
| ---- | ---------------------------------------- |
| `qa` | `a` kayıt alanına makro kaydetmeye başla |
| `@a` | `a` kayıt alanındaki makroyu çalıştır    |
| `@@` | Son kullanılan makroyu tekrar et         |
```


##### Topluluk ve Belgeleme
Neovim, aktif bir topluluğa ve zengin bir belgeleme kaynağına sahiptir. Karşılaştığınız herhangi bir sorunla ilgili destek almak çok kolaydır; topluluk forumları, GitHub depoları ve kılavuzlar sayesinde çözüm bulabilirsiniz.

##### Daha Derin Bir Bağlantı
Neovim kullanmak, araçlarınızla daha derin bir bağlantı kurmanıza yardımcı olur. Kendi tuş eşlemelerinizi ve eklentilerinizi oluşturmak, kodlama sürecinizi bir ustalık seviyesine taşır. Bu özelleştirmeler, çalışma tarzınıza en uygun hale getirilmiş bir ortam yaratmanıza olanak tanır, böylece verimliliğinizi ve iş akışınızı iyileştirirsiniz.

##### Sonuç
Neovim, basit bir metin düzenleyiciden çok daha fazlasıdır—geliştiricilere iş akışlarında tam kontrol ve özgürlük sunar. Eğer geliştirme sürecinizi iyileştirmek ve daha minimal bir deneyim yaşamak istiyorsanız, kesinlikle Neovim'i denemelisiniz. Bu araç, özelleştirme seçenekleri ve verimli çalışma imkanı ile kodlama deneyiminizi daha keyifli ve etkili hale getirebilir.
