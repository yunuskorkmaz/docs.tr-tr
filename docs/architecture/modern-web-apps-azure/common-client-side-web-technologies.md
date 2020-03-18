---
title: Ortak istemci tarafı web teknolojileri
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Ortak istemci tarafı web teknolojileri
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2809c8539b42e8e2250039dceed1389b3cbdcd8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449380"
---
# <a name="common-client-side-web-technologies"></a>Ortak istemci tarafı web teknolojileri

> "Web siteleri içeriden ve dışarıdan iyi görünmelidir."  
> _- Paul Cookson_

ASP.NET Çekirdek uygulamaları web uygulamalarıdır ve genellikle HTML, CSS ve JavaScript gibi istemci tarafındaki web teknolojilerine güvenirler. Karmaşık web uygulamaları, sayfanın (HTML) içeriğini düzeninden ve stilinden (CSS) ve davranışından (JavaScript aracılığıyla) ayırarak, Endişelerin Ayrılması ilkesinden yararlanabilir. Uygulamanın yapısında, tasarımında veya davranışında gelecekteki değişiklikler, bu endişeler iç içe geçtiğinde daha kolay yapılabilir.

HTML ve CSS nispeten kararlı olsa da, JavaScript, uygulama çerçeveleri ve yardımcı programlar geliştiriciler için ürünün web tabanlı uygulamalar ışıklamak için çalışmaları sayesinde, son derece hızla gelişmekte olmuştur. Bu bölümde, JavaScript'in web geliştiricileri tarafından kullanıldığı birkaç yöntem eðerlenir ve Açıl ve Tepki istemci tarafý kitaplýklarýna üst düzey bir genel bakış sunar.

> [!NOTE]
> Blazor zengin, etkileşimli istemci kullanıcı arabirimleri oluşturmak için JavaScript çerçeveleri için bir alternatif sağlar. İstemci tarafı Blazor desteği hala önizlemede, bu nedenle şimdilik bu bölümün kapsamı dışında.

## <a name="html"></a>HTML

HTML, web sayfaları ve web uygulamaları oluşturmak için kullanılan standart biçimlendirme dilidir. Öğeleri, biçimlendirilmiş metni, görüntüleri, form girişlerini ve diğer yapıları temsil eden sayfaların yapı taşlarını oluşturur. Bir tarayıcı bir URL'ye istekte bulununca, ister bir sayfa ister uygulama getirin, döndürülen ilk şey bir HTML belgesidir. Bu HTML belgesi, görünümü ve düzeni hakkında CSS biçiminde ek bilgiler veya JavaScript biçiminde ki davranışlara başvurabilir veya ek bilgiler içerebilir.

## <a name="css"></a>CSS

CSS (Basamaklı Stil Sayfaları), HTML öğelerinin görünümünü ve düzenini denetlemek için kullanılır. CSS stilleri, aynı sayfada ayrı olarak tanımlanan veya ayrı bir dosyada tanımlanan ve sayfa tarafından başvurulan bir HTML öğesine doğrudan uygulanabilir. Belirli bir HTML öğesini seçmek için nasıl kullanıldıklarına bağlı olarak stiller basamaklanır. Örneğin, bir stil belgenin tamamına uygulanabilir, ancak belirli bir öğeye uygulanan bir stil tarafından geçersiz kılınabilir. Aynı şekilde, öğeye özgü bir stil, öğeye uygulanan bir CSS sınıfına uygulanan ve bu öğenin belirli bir örneğini (kimliği üzerinden) hedefleyen bir stil tarafından geçersiz kılınan bir stil tarafından geçersiz kılınacak şekilde geçersiz kılınmıştır. Şekil 6-1

![CSS Özgüllük kuralları](./media/image6-1.png)

**Şekil 6-1.** Sırayla CSS Özgüllük kuralları.

Stilleri kendi ayrı stil sayfası dosyalarında tutmak ve uygulama içinde tutarlı ve yeniden kullanılabilir stilleri uygulamak için seçim tabanlı basamaklama kullanmak en iyisidir. HTML içinde stil kuralları yerleştirmekten kaçınılmalıdır ve stilleri belirli tek tek öğelere (tüm öğe sınıfları veya bunlara uygulanan belirli bir CSS sınıfı olan öğeler yerine) uygulamak kural değil, istisna olmalıdır.

### <a name="css-preprocessors"></a>CSS ön işlemcileri

CSS stil sayfaları koşullu mantık, değişkenler ve diğer programlama dili özellikleri için destek eksikliği. Bu nedenle, html öğeleri ve CSS sınıflarının birçok farklı varyasyonuna aynı renk, yazı tipi veya başka bir ayar uygulandığından, büyük stil sayfaları genellikle biraz yineleme içerir. CSS önişlemcileri, değişkenler ve mantık desteği ekleyerek stil sayfalarınızın [DRY ilkesini](https://deviq.com/don-t-repeat-yourself/) izlemesine yardımcı olabilir.

En popüler CSS önişlemciler Sass ve LESS vardır. Her ikisi de CSS genişletmek ve onunla geriye doğru uyumlu, düz bir CSS dosyası geçerli bir Sass veya LESS dosyası olduğu anlamına gelir. Sass Ruby tabanlı ve DAHA AZ JavaScript tabanlı ve her ikisi de genellikle yerel geliştirme sürecinin bir parçası olarak çalıştırın. Her ikiside de komut satırı araçlarının yanı sıra Visual Studio'da Gulp veya Grunt görevlerini kullanarak çalıştırmak için yerleşik destek bulunmaktadır.

## <a name="javascript"></a>JavaScript

JavaScript, ECMAScript dil belirtiminde standartlaştırılmış dinamik, yorumlanmış bir programlama dilidir. Bu web programlama dilidir. CSS gibi, JavaScript de HTML öğeleri içindeki öznitelikler, bir sayfa içinde veya ayrı dosyalarda komut dosyası blokları olarak tanımlanabilir. CSS gibi, JavaScript'i de ayrı dosyalar halinde düzenlemek ve tek tek web sayfalarında veya uygulama görünümlerinde bulunan HTML'den mümkün olduğunca ayrı tutulması önerilir.

Web uygulamanızda JavaScript ile çalışırken, sık sık gerçekleştirmeniz gereken birkaç görev vardır:

- Bir HTML öğesi seçmek ve değerini almak ve/veya güncellemek.

- Veri için Web API'si sorgulama.

- Web API'sine komut gönderme (ve sonucuyla birlikte geri arama yanıtı).

- Doğrulama gerçekleştirme.

Bu görevlerin tümlerini yalnızca JavaScript ile gerçekleştirebilirsiniz, ancak bu görevleri kolaylaştırmak için birçok kitaplık vardır. Bu kütüphanelerin ilk ve en başarılı biri web sayfalarında bu görevleri basitleştirmek için popüler bir seçim olmaya devam ediyor jQuery vardır. Tek Sayfauygulamaları (SPA'lar) için jQuery, Açısal ve React'in sunduğu istenilen özelliklerin çoğunu sağlamaz.

### <a name="legacy-web-apps-with-jquery"></a>jQuery ile eski web uygulamaları

JavaScript çerçeve standartlarına göre eski olmasına rağmen, jQuery HTML / CSS ve web API'lar IÇIN AJAX aramaları yapmak uygulamaları bina ile çalışmak için yaygın olarak kullanılan bir kütüphane olmaya devam etmektedir. Ancak, jQuery tarayıcı belge nesne modeli (DOM) düzeyinde çalışır ve varsayılan olarak yalnızca bir zorunluluk sunuyor, yerine bildirimsel, model.

Örneğin, bir textbox'ın değeri 10'u aşarsa, sayfadaki bir öğenin görünür hale getirilmesi gerektiğini düşünün. jQuery'de bu genellikle textbox değerini denetleyecek ve hedef öğenin görünürlüğünü bu değere göre ayarlayan kodlu bir olay işleyicisi yazılarak uygulanır. Bu zorunlu, kod tabanlı bir yaklaşımdır. Başka bir çerçeve bunun yerine, öğenin görünürlüğünü bildirimsel olarak textbox değerine bağlamak için veri bağlama yı kullanabilir. Bu herhangi bir kod yazmayı gerektirmez, ancak bunun yerine yalnızca veri bağlama öznitelikleri ile ilgili öğeleri dekorasyon gerektirir. İstemci tarafı davranışları daha karmaşık hale geldikçe, veri bağlama yaklaşımları sıklıkla daha az kod ve koşullu karmaşıklıkla daha basit çözümlerle sonuçlanır.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs bir SPA Çerçevesi

| **Faktörü** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| SOYUTLAR DOM | **Evet** | **Evet** |
| AJAX Desteği | **Evet** | **Evet** |
| Bildirimsel Veri Bağlama | **Hayır** | **Evet** |
| MVC tarzı Yönlendirme | **Hayır** | **Evet** |
| Templating | **Hayır** | **Evet** |
| Derin Bağlantı Yönlendirme | **Hayır** | **Evet** |

JQuery'nin eksik olduğu özelliklerin çoğu diğer kütüphanelerin eklenmesiyle eklenebilir. Ancak, Açısal gibi bir SPA çerçevesi, başından beri hepsi göz önünde bulundurularak tasarlandığı için bu özellikleri daha entegre bir şekilde sunar. Ayrıca, jQuery zorunlu bir kütüphane, jQuery ile bir şey yapmak için jQuery işlevleri aramak gerekir anlamına gelir. SPA çerçevelerinin sağladığı iş ve işlevlerin çoğu, gerçek bir kod yazılmayı gerektirmeyerek bildirimsel olarak yapılabilir.

Veri bağlama bunun büyük bir örneğidir. jQuery'de, bir DOM öğesinin değerini almak veya bir öğenin değerini ayarlamak için genellikle yalnızca bir kod satırı alır. Ancak, öğenin değerini değiştirmeniz gerektiğinde bu kodu yazmanız gerekir ve bazen bu bir sayfadaki birden çok işlevde oluşur. Başka bir yaygın örnek eleman görünürlüğüdür. jQuery'de, belirli öğelerin görünür olup olmadığını denetlemek için kod yazacağınız birçok farklı yer olabilir. Bu durumların her birinde, veri bağlama kullanırken, hiçbir kod yazılması gerekmez. Söz konusu öğelerin değerini veya görünürlüğünü sayfadaki bir *görünüm modeline* bağlamanız yeterlidir ve bu görünüm modelindeki değişiklikler bağlı öğelere otomatik olarak yansıtılır.

### <a name="angular-spas"></a>Açısal SP'ler

Açısal dünyanın en popüler JavaScript çerçevelerinden biri olmaya devam etmektedir. Açısal 2'den bu yana, ekip çerçeveyi sıfırdan yeniden [(TypeScript](https://www.typescriptlang.org/)kullanarak) yeniden oluşturmuş ve orijinal Açısal JS adından yalnızca Açısal olarak yeniden markalaşmıştır. Şimdi birkaç yaşında, yeniden tasarlanmış Açısal Tek Sayfa Uygulamaları oluşturmak için sağlam bir çerçeve olmaya devam ediyor.

Açısal uygulamalar bileşenlerden oluşturulur. Bileşenler HTML şablonlarını özel nesnelerle birleştirir ve sayfanın bir bölümünü denetler. Açısal'ın dokümanlarından basit bir bileşen burada gösterilmiştir:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Bileşenler, bileşen @Component hakkında meta veri alan dekoratör işlevi kullanılarak tanımlanır. Seçici özellik, bu bileşenin görüntüleneceği sayfadaki öğenin kimliğini tanımlar. Şablon özelliği, bileşenin son satırda tanımlanan ad özelliğine karşılık gelen bir yer tutucu içeren basit bir HTML şablonudur.

Dom öğeleri yerine bileşenler ve şablonlarla çalışarak, Açısal uygulamalar daha yüksek bir soyutlama düzeyinde ve yalnızca JavaScript ("vanilya JS" olarak da adlandırılır) veya jQuery ile yazılmış uygulamalardan daha az genel kodla çalışabilir. Açısal ayrıca istemci tarafındaki komut dosyası dosyalarınızı nasıl düzenlediğinize ilişkin bazı komut dosyaları da uygular. Kuralına göre, Açısal uygulamalar, bir uygulama klasöründe bulunan modül ve bileşen komut dosyası dosyalarıyla ortak bir klasör yapısı kullanır. Uygulamayı oluşturma, dağıtma ve sınama ile ilgili açısal komut dosyaları genellikle daha üst düzey bir klasörde bulunur.

Bir CLI kullanarak Açısal uygulamalar geliştirebilirsiniz. Yerel Açısal geliştirme ile başlarken (zaten git ve npm yüklü varsayarak) sadece GitHub bir `npm install` `npm start`repo klonlama ve çalışan ve oluşur . Bunun ötesinde, Açısal gemiler projeler oluşturabilir, dosya ekleyebilir ve sınama, birleştirme ve dağıtım görevlerine yardımcı olabilir. Bu CLI dostu, Açısal'ı özellikle harika CLI desteğine sahip ASP.NET Core ile uyumlu hale getirir.

Microsoft bir referans uygulaması geliştirdi, [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), Açısal SPA uygulaması içeren. Bu uygulama, çevrimiçi mağazanın alışveriş sepetini yönetmek, kataloğundan öğeleri yüklemek ve görüntülemek ve sipariş oluşturma yı işlemek için Açısal modüller içerir. Örnek uygulamayı [GitHub'dan](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA)görüntüleyebilir ve indirebilirsiniz.

### <a name="react"></a>React

Tam bir Model-View-Controller desen uygulaması sunan Açısal'ın aksine, React yalnızca görünümlerle ilgilidir. Bu bir çerçeve değil, sadece bir kütüphane, bu nedenle ek kütüphaneler kaldıraç gerekir bir SPA oluşturmak için gerekir. Zengin tek sayfauygulamaları üretmek için React ile kullanılmak üzere tasarlanmış kütüphaneler vardır.

React'in en önemli özelliklerinden biri sanal BIR DOM kullanmasıdır. Sanal DOM performans (sanal DOM gerçek DOM hangi bölümleri güncellenmesi gerekir optimize edebilirsiniz) ve test edilebilirlik (gerek React ve sanal DOM ile etkileşimleri test etmek için bir tarayıcı olması gerekmez) dahil olmak üzere çeşitli avantajlar ile React sağlar.

Tepki html ile nasıl çalıştığını da alışılmadık. Kod ve biçimlendirme arasında katı bir ayrım yapmak yerine (HTML özniteliklerinde görünen JavaScript'e yapılan atıflar ile), React HTML'yi doğrudan JavaScript koduna JSX olarak ekler. JSX, saf JavaScript'e kadar derlenebilen HTML benzeri sözdizimidir. Örnek:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Zaten JavaScript biliyorsanız, React öğrenme kolay olmalıdır. Açısal veya diğer popüler kütüphaneler ile ilgili neredeyse çok fazla öğrenme eğrisi veya özel sözdizimi yoktur.

React tam bir çerçeve olmadığından, genellikle yönlendirme, web API çağrıları ve bağımlılık yönetimi gibi şeyleri diğer kitaplıkların işlemesini istersiniz. Güzel şey, bunların her biri için en iyi kütüphane seçebilirsiniz, ama dezavantajı tüm bu kararları almak ve işiniz bittiğinde seçtiğiniz tüm kütüphaneler birlikte iyi çalıştığını doğrulamak gerekir. İyi bir başlangıç noktası istiyorsanız, React Slingshot gibi bir başlangıç kiti kullanabilirsiniz, bu da react ile birlikte uyumlu kitaplıklar kümesini önceden paketler.

### <a name="vue"></a>Vue

Onun başlangıç kılavuzu itibaren, "Vue kullanıcı arayüzleri oluşturmak için ilerici bir çerçevedir. Diğer yekpare çerçevelerin aksine, Vue sıfırdan kademeli olarak benimsenebilir olarak tasarlanmıştır. Çekirdek kitaplık yalnızca görünüm katmanına odaklanmıştır ve diğer kitaplıkları veya varolan projelerle kolayca karşılanır ve bu katmanla tümleştirebilirsiniz. Öte yandan Vue, modern takım ve destekleyici kütüphanelerle birlikte kullanıldığında gelişmiş Tek Sayfauygulamaları'na mükemmel bir şekilde güç verebilmiştir."

Vue ile başlarken sadece bir HTML dosyası içinde komut dosyası dahil gerektirir:

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

Eklenen çerçeveyle, Vue'nun basit cezbedici sözdizimini kullanarak DOM'a bildirimsel olarak veri işleebilirsiniz:

```html
<div id="app">
  {{ message }}
</div>
```

ve sonra aşağıdaki komut dosyası ekleyerek:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

Bu "Merhaba Vue!" işlemek için yeterlidir. sayfada. Ancak, Vue'nun mesajı sadece bir kez div'e iletmediğine dikkat edin. Veri bağlama ve dinamik güncelleştirmeleri destekler, `message` örneğin değişikliklerin değeri, değeri yansıtacak şekilde hemen `<div>` güncelleştirilir.

Tabii ki, bu sadece Vue'nun yapabileceklerinin yüzeyini çizer. Bu son birkaç yıl içinde popülerlik büyük bir kazandı ve büyük bir topluluk var. Vue ile birlikte çalışarak bunu genişletmek için çalışan [büyük ve büyüyen bir destek bileşenleri ve kütüphaneler listesi](https://github.com/vuejs/awesome-vue#redux) vardır. Web uygulamanıza istemci tarafı davranışı eklemek veya tam bir SPA oluşturmayı düşünüyorsanız, Vue araştırmaya değer.

### <a name="choosing-a-spa-framework"></a>SPA Çerçevesi Seçimi

Spa'nızı desteklemek için hangi JavaScript çerçevesinin en iyi şekilde çalışacağını düşünürken, aşağıdaki hususları göz önünde bulundurun:

- Ekibiniz çerçeveyi ve bağımlılıklarını biliyor mu (bazı durumlarda TypeScript dahil)?

- Çerçeve ne kadar dik kafalı ve onun varsayılan şeyler yapma şekline katılıyor musunuz?

- Uygulamanızın gerektirdiği tüm özellikleri içeriyor mu (veya bir yardımcı kitaplık) içeriyor mu?

- İyi belgelenmiş mi?

- Topluluğu ne kadar aktif? Yeni projeler bununla mı inşa ediliyor?

- Çekirdek ekibi ne kadar aktif? Sorunlar çözülür ve yeni sürümler düzenli olarak sevk ediliyor mu?

JavaScript çerçeveleri aşırı hız ile gelişmeye devam ediyor. Daha sonra bağımlı olmaktan pişman olacağınız bir çerçeve seçme riskini azaltmaya yardımcı olmak için yukarıda listelenen hususları kullanın. Özellikle riskten kaçınıyorsanız, ticari destek sunan ve/veya büyük bir kuruluş tarafından geliştirilmekte olan bir çerçeve düşünün.

> ### <a name="references--client-web-technologies"></a>Referanslar – Müşteri Web Teknolojileri
>
> - **HTML ve CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs DAHA AZ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Daha AZ, Sass ve Font Awesome ile ASP.NET Core Apps Şekillendirme**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **ASP.NET Çekirdekte Müşteri-Yan Geliştirme**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://reactjs.org/>
> - **Vue**  
> <https://vuejs.org/>
> - **Açısal vs Tepki vs Vue: 2020 yılında hangi Çerçeve seçilecek**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/>
> - **2020'de Ön Uç Geliştirme için En İyi JavaScript Çerçeveleri**  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
>[Önceki](common-web-application-architectures.md)
>[Sonraki](develop-asp-net-core-mvc-apps.md)
