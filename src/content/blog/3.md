---
title: 'TanStack Nedir, Ne İşe Yarar ve Neden Kullanmalıyız?'
description: 'Tanstack'
pubDate: 'May 10 2025'
heroImage: '/tanstack.png'
---

Modern frontend geliştirme süreçlerinde, veri ile çalışmak kaçınılmazdır. Kullanıcı tablolarla veri görmek, filtrelemek, sıralamak ve sayfalamak ister. Ancak bu özellikleri sıfırdan geliştirmek zaman alır ve sürdürülebilir olmaz. İşte bu noktada TanStack devreye giriyor.

##### TanStack Nedir?

[TanStack](https://tanstack.com/query/latest/docs/framework/react/overview) , farklı web teknolojileri için hazırlanmış, veri yönetimini kolaylaştıran açık kaynak kütüphaneler topluluğudur. En bilinenleri şunlardır:


  - TanStack Table – Önceden React Table olarak bilinen, framework bağımsız (React, Vue, Solid, Svelte) tablo çözümü.

  - TanStack Query – Sunucudan veri çekme, cache’leme ve senkronizasyon yönetimi (önceden React Query).

  - TanStack Virtual – Büyük listelerin ve tabloların performanslı şekilde gösterilmesini sağlar (sanal kaydırma).

  - TanStack Router – Uygulamalar için güçlü ve esnek bir router çözümü (özellikle React ile güçlü entegrasyon).

##### Ne İşe Yarar?
Özellikle büyük projelerde, veri ile çalışan bileşenleri oluştururken sıklıkla şu sorunlarla karşılaşırız:

  - Tablolarda sayfalama, sıralama, filtreleme

  - API'den veri çekme ve güncel tutma

  - Scroll performans problemleri

  - Karmaşık route yapılarının yönetimi

TanStack kütüphaneleri bu problemleri çözmek için minimal, esnek ve performans odaklı araçlar sunar.

##### Neden TanStack Kullanmalıyız?
1. **Performans**

TanStack Virtual gibi çözümlerle, binlerce veriyi sanal olarak göstererek DOM yorgunluğunu azaltır. Kullanıcıya hızlı ve akıcı bir deneyim sunar.

2. **Modüler Yapı**

Her bir kütüphane tek bir amaca hizmet eder. İstediğini alır, istemediğini kullanmazsın. Bu da projeni şişirmeden özelleştirmeni sağlar.

3. **Framework Bağımsızlık**

TanStack Table gibi kütüphaneler React ile başladı ama artık Vue, Solid ve Svelte ile de çalışabiliyor.

4. **Server-State Yönetimi (TanStack Query)**

React Query sayesinde, veri çekme işlemleri tekrar tekrar yazılmak zorunda kalmaz. Otomatik cache, refetching, polling gibi özellikler projeye entegre olur.

5. **Dokümantasyon ve Topluluk**

TanStack'in çok iyi belgelenmiş bir yapısı ve geniş bir topluluğu vardır. Sık yaşanan sorunlara kolayca çözüm bulmak mümkündür.
Nerelerde Kullanılır?

  - Admin panelleri ve dashboard uygulamaları

  - CRM ve ERP sistemleri

  - E-ticaret filtreleme sistemleri

  - API ile çalışan tablolar

  - SSR veya CSR projeler


##### TanStack Query Kullanımı
1. **Gerekli paketleri kur**

```bash
npm install @tanstack/react-query
```

2. **App.jsx dosyasında QueryClient kurulumunu yap**
```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import App from './App';

const queryClient = new QueryClient();

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <QueryClientProvider client={queryClient}>
      <App />
    </QueryClientProvider>
  </React.StrictMode>
);
```

3. **App.jsx içinde veri çekme işlemi**
```js
import { useQuery } from '@tanstack/react-query';
import axios from 'axios';

const fetchPosts = async () => {
  const { data } = await axios.get('https://jsonplaceholder.typicode.com/posts');
  return data;
};

function App() {
  const { data, isLoading, isError, error } = useQuery({
    queryKey: ['posts'],
    queryFn: fetchPosts,
  });

  if (isLoading) return <p>Yükleniyor...</p>;
  if (isError) return <p>Hata: {error.message}</p>;

  return (
    <div>
      <h1>Postlar</h1>
      <ul>
        {data.map((post) => (
          <li key={post.id}>
            <strong>{post.title}</strong>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

##### Açıklamalar:
  - **useQuery:** API'den veri çekmek için kullanılır.
  - **queryKey:** Cache anahtarıdır. Aynı key ile yapılan sorgular tekrar API'ye gitmeden cache’ten gelir.
  - **queryFn:** Asenkron veri getiren fonksiyondur (örneğin axios ile API çağrısı).
  - **isLoading**, **isError**, **data**, **error:** Sorgu durumları için kullanılabilecek otomatik flag’lerdir.
