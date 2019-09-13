---
title: Ortak istemci tarafı web teknolojileri
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın Ortak istemci tarafı Web teknolojileri
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 4dd747293fba4c18c2d10738d36f4d98cfd3f5b9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926495"
---
# <a name="common-client-side-web-technologies"></a>Ortak istemci tarafı web teknolojileri

> "Web siteleri, iç ve çıkış arasında iyi görünmelidir."  
> _-Paul pişirme son_

ASP.NET Core uygulamalar Web uygulamalardır ve genellikle HTML, CSS ve JavaScript gibi istemci tarafı Web teknolojilerine bağımlıdır. Sayfa (HTML) içeriğini düzen ve stil (CSS) ve davranışını (JavaScript aracılığıyla) ayırarak, karmaşık Web uygulamaları, endişeleri ayrımı özelliğinden yararlanabilir. Uygulamanın yapısı, tasarımı veya davranışında yapılacak değişiklikler, bu konular intertwined olmadığında daha kolay hale getirilebilir.

HTML ve CSS görece kararlı olsa da, JavaScript, uygulama çerçeveleri ve yardımcı programlar tarafından Web tabanlı uygulamalar oluşturmak için birlikte çalışarak,, Breakneck hızında gelişiyor. Bu bölüm, JavaScript 'in Web geliştiricileri tarafından uygulama geliştirme kapsamında kullanıldığı, angular ve istemci tarafı kitaplıklarına yanıt verme konusunda üst düzey bir genel bakış sunan bazı yöntemlere bakar.

## <a name="html"></a>HTML

HTML (köprü metni biçimlendirme dili), Web sayfaları ve Web uygulamaları oluşturmak için kullanılan standart biçimlendirme dilidir. Öğeleri, biçimlendirilen metin, görüntüler, form girişleri ve diğer yapıları temsil eden sayfa oluşturma blokları oluşturuyor. Bir tarayıcı bir URL 'ye istek yaptığında, bir sayfa veya uygulama döndürmeksizin döndürülen ilk şey bir HTML belgesidir. Bu HTML belgesi, CSS biçimindeki görünüm ve düzen ile ilgili ek bilgilere başvurabilir veya JavaScript biçiminde davranış gösterebilir.

## <a name="css"></a>CSS

CSS (Geçişli Stil Sayfaları), HTML öğelerinin görünüm ve yerleşimini denetlemek için kullanılır. CSS stilleri, aynı sayfada ayrı olarak tanımlanan veya ayrı bir dosyada tanımlanmış ve sayfa tarafından başvurulan bir HTML öğesine doğrudan uygulanabilir. Stiller, belirli bir HTML öğesini seçmek için nasıl kullanıldığına göre basamaklandırılır. Örneğin, bir stil tüm belgeye uygulanabilir, ancak belirli bir öğeye uygulanan bir stil tarafından geçersiz kılınır. Benzer şekilde, öğeye özgü bir stil, öğesine uygulanan bir CSS sınıfına uygulanan bir stil tarafından geçersiz kılınır. Bu, sırasıyla bu öğenin belirli bir örneğini hedefleyen bir stil tarafından geçersiz kılınır (kimliği aracılığıyla). Şekil 6-1

![CSS specificity kuralları](./media/image6-1.png)

**Şekil 6-1.** CSS specificity kuralları, sırasıyla.

Stilleri kendi ayrı stil sayfası dosyalarında tutmak ve uygulama içinde tutarlı ve yeniden kullanılabilir stilleri uygulamak için seçim tabanlı basamaklama kullanmak en iyisidir. Stil kurallarının HTML içine yerleştirilmesi kaçınılmalıdır ve belirli tek öğelerin (tüm öğelerin sınıfları yerine veya kendilerine uygulanan belirli bir CSS sınıfına sahip olan öğelerin) uygulanması, kural değil özel durum olmalıdır.

### <a name="css-preprocessors"></a>CSS önişlemcisi

CSS stil sayfalarında koşullu mantık, değişkenler ve diğer programlama dili özellikleri için destek yoktur. Bu nedenle, birçok farklı HTML ve CSS sınıfı çeşitlemelerine aynı renk, yazı tipi veya diğer ayarlar uygulandığından büyük stil sayfaları genellikle çok fazla yineleme içerir. CSS önişlemcisi, stil sayfalarınızın ve mantığa yönelik destek ekleyerek [kurutma ilkesini](https://deviq.com/don-t-repeat-yourself/) takip etmenize yardımcı olabilir.

En popüler CSS önişlemcisi Sass ve küçüktür. Her ikisi de CSS 'yi genişletir ve bununla birlikte, düz bir CSS dosyasının geçerli bir Sass veya daha az dosya olduğu anlamına gelir. Sass, Ruby tabanlıdır ve JavaScript tabanlıdır ve genellikle yerel geliştirme işleminizin bir parçası olarak çalışır. Hem komut satırı araçlarının hem de Gulp ya da Grreki görevleri kullanılarak çalıştırılması için Visual Studio 'da yerleşik destek bulunur.

## <a name="javascript"></a>JavaScript

JavaScript, ECMAScript dil belirtiminde standartlaştırılmış olan dinamik, yorumlanan bir programlama dilidir. Web 'in programlama dilidir. CSS gibi JavaScript, HTML öğeleri içinde, bir sayfa içinde betik blokları olarak veya ayrı dosyalarda öznitelik olarak tanımlanabilir. CSS gibi, genellikle JavaScript 'i ayrı dosyalara düzenlemeniz önerilir ve bu, ayrı Web sayfalarında veya uygulama görünümlerinde bulunan HTML 'den mümkün olduğunca ayrılmaktadır.

Web uygulamanızda JavaScript ile çalışırken, genellikle gerçekleştirmeniz gereken birkaç görev vardır:

- Bir HTML öğesi seçme ve değerini alma ve/veya güncelleştirme.

- Bir Web API 'sini veri için sorgulama.

- Bir Web API 'sine komut gönderme (ve sonucuyla birlikte geri çağırmaya yanıt verme).

- Doğrulama gerçekleştiriliyor.

Bu görevlerin tümünü tek başına JavaScript ile gerçekleştirebilirsiniz, ancak bu görevleri daha kolay hale getirmek için birçok kitaplık vardır. Bu kitaplıkların ilk ve en başarılı olanı, Web sayfalarında bu görevleri basitleştirmek için popüler bir seçenek olmaya devam eden jQuery 'dir. Tek sayfalı uygulamalar (maça 'Lar) için jQuery, istenen özelliklerin çoğunu angular ve tepki veren bir şekilde sunmaz.

### <a name="legacy-web-apps-with-jquery"></a>JQuery ile eski Web uygulamaları

JavaScript Framework standartlarına göre, jQuery, HTML/CSS ile çalışmaya ve Web API 'Lerine AJAX çağrıları yapan uygulamalar oluşturmaya yönelik çok yaygın olarak kullanılan bir kitaplık olmaya devam etmektedir. Bununla birlikte, jQuery, tarayıcı belgesi nesne modeli (DOM) düzeyinde çalışır ve varsayılan olarak, bildirim temelli model yerine yalnızca bir kesinlik sağlar.

Örneğin, bir TextBox değeri 10 ' u aşarsa sayfadaki bir öğenin görünür hale getirilmesinin gerektiği hakkında düşünün. JQuery 'ta bu, genellikle TextBox 'ın değerini inceleyerek ve hedef öğenin görünürlüğünü bu değere göre ayarlayabilecek kodla bir olay işleyicisi yazılarak uygulanır. Bu, zorunlu, kod tabanlı bir yaklaşımdır. Bunun yerine başka bir çerçeve, öğesinin görünürlüğünü bildirimli olarak metin değerine bağlamak için veri bağlamayı kullanabilir. Bu, herhangi bir kod yazmayı gerektirmez, ancak bunun yerine yalnızca veri bağlama öznitelikleriyle ilgili öğeleri dekoratmayı gerektirir. İstemci tarafı davranışları daha karmaşık büyürken, veri bağlama yaklaşımları genellikle daha az kod ve koşullu karmaşıklıkla daha basit çözümlere neden olacak.

### <a name="jquery-vs-a-spa-framework"></a>jQuery ile SPA çerçevesi karşılaştırması

| **Çarpan** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| DOM 'ı soyutlar | **Evet** | **Evet** |
| AJAX desteği | **Evet** | **Evet** |
| Bildirime dayalı veri bağlama | **Eşleşen** | **Evet** |
| MVC stili yönlendirme | **Eşleşen** | **Evet** |
| Örneğine | **Eşleşen** | **Evet** |
| Derin bağlantı yönlendirme | **Eşleşen** | **Evet** |

JQuery eksik doğası gereği özelliklerinin çoğu diğer kitaplıkların eklenmesiyle eklenebilir. Ancak, angular gibi bir SPA çerçevesi, başlangıçtan itibaren göz önünde bulundurularak tasarlandığından, bu özellikleri daha tümleşik bir biçimde sunar. Ayrıca, jQuery, jQuery ile herhangi bir şey yapmak için jQuery işlevlerini çağırmanız gereken çok kesinlik içeren bir kitaplıktır. SPA çerçevelerinin sağladığı iş ve işlevselliğin çoğu bildirimli olarak yapılabilir ve hiçbir gerçek kod yazılmasına gerek yoktur.

Veri bağlama buna harika bir örnektir. JQuery 'ta, genellikle bir DOM öğesinin değerini almak veya bir öğenin değerini ayarlamak için yalnızca tek bir kod satırı alır. Ancak, bu kodu, öğenin değerini değiştirmeniz gereken her seferinde yazmanız gerekir ve bazen bu, bir sayfada birden çok işlev ile gerçekleşir. Diğer bir yaygın örnek, öğe görünürlüğüne sahiptir. JQuery 'de, belirli öğelerin görünür olup olmadığını denetlemek için kod yazacağınız birçok farklı yer olabilir. Bu durumların her birinde, veri bağlamayı kullanırken, hiçbir kodun yazılması gerekmez. Söz konusu öğe (ler) in değerini veya görünürlüğünü sayfadaki bir *ViewModel* 'e bağlamanız yeterlidir ve bu ViewModel üzerindeki değişiklikler otomatik olarak bağlı öğelerde yansıtılır.

### <a name="angular-spas"></a>Angular maça 'Ları

AngularJS, dünyanın en popüler JavaScript çerçevelerinden bir hızla gelmiştir. Angular 2 ile, ekip çerçeveyi baştan sona yeniden oluşturur ( [TypeScript](https://www.typescriptlang.org/)kullanarak) ve AngularJS 'Den yalnızca angular 'e yeniden markalı olur. Şu anda sürüm 4 ' te, angular tek sayfalı uygulamalar oluşturmaya yönelik sağlam bir çerçeve olmaya devam etmektedir.

Angular uygulamaları bileşenlerden oluşturulmuştur. Bileşenler, HTML şablonlarını özel nesnelerle birleştirir ve sayfanın bir bölümünü kontrol edin. Angular belgelerinden basit bir bileşen aşağıda gösterilmiştir:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Bileşenler, bileşen hakkında meta @Component veriler alan dekoratör işlevi kullanılarak tanımlanır. Selector özelliği, bu bileşenin görüntüleneceği sayfadaki öğenin kimliğini tanımlar. Şablon özelliği, son satırda tanımlanan bileşen adı özelliğine karşılık gelen bir yer tutucu içeren basit bir HTML şablonudur.

DOM öğeleri yerine bileşenler ve şablonlar ile çalışarak, angular uygulamaları daha yüksek bir soyutlama düzeyinde ve yalnızca JavaScript ("Vanilla JS" olarak da bilinir) kullanılarak yazılmış uygulamalardan veya jQuery ile daha az genel kodla çalışabilir. Angular Ayrıca, istemci tarafı betik dosyalarınızı düzenleme konusunda bir sıralama uygular. Kurala göre, angular uygulamaları, bir uygulama klasöründe bulunan modül ve bileşen komut dosyaları ile ortak bir klasör yapısı kullanır. Uygulama oluşturma, dağıtma ve test etme ile ilgili angular betikleri genellikle daha yüksek düzey bir klasörde bulunur.

Angular ayrıca komut satırı arabirimi (CLı) araçlarının harika bir şekilde kullanılmasını sağlar. Angular geliştirmeyi yerel olarak kullanmaya başlama (git ve NPM 'nin yüklü olduğu varsayılarak), GitHub 'dan ve çalıştıran `npm install` `npm start`bir depoyu klonlamalarından oluşur. Bunun ötesinde, angular, proje oluşturabileceğiniz, dosya ekleyen ve test etme, paketleme ve dağıtım görevlerine yardımcı olan kendi CLı aracını dağıtırın. Bu CLı araçları, özellikle de ASP.NET Core ile uyumlu olan ve harika CLı desteği sunan bir fikir sunar.

Microsoft, angular SPA uygulaması içeren bir başvuru uygulaması ( [Eshoponcontainers](https://aka.ms/MicroservicesArchitecture)) geliştirmiştir. Bu uygulama, çevrimiçi mağaza alışveriş sepetini yönetmek, kataloğundan öğeleri yüklemek ve göstermek ve sipariş oluşturmayı işlemek için angular modüllerini içerir. Örnek uygulamayı [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA)' dan görüntüleyebilir ve indirebilirsiniz.

### <a name="react"></a>React

Tam model-görünüm-denetleyici modeli uygulamasını sunan angular 'ın aksine, yanıt verme yalnızca görünümlerle ilgilidir. Yalnızca bir kitaplık değildir, bu nedenle bir SPA oluşturmak için ek kitaplıkların olması gerekir.

Yanıt verme 'nın en önemli özelliklerinden biri, sanal DOM 'ın kullanımı. Sanal DOM, performans dahil olmak üzere çeşitli avantajlar sağlar (sanal DOM gerçek DOM 'ın hangi bölümlerinin güncelleştirileceğini en iyi hale getirebilir) ve tekararlılığı (yanıt verme ve sanal DOM ile etkileşimlerini test etmek için bir tarayıcıya gerek yoktur).

Ayrıca, HTML ile nasıl çalıştığı konusunda da olağan dışı tepki verir. Kod ve biçimlendirme arasında (Belki de HTML özniteliklerde görünen JavaScript başvuruları ile) kesin bir ayrım yapmak yerine, yanıt olarak HTML 'yi doğrudan kendi JavaScript kodu içinde JSX olarak ekler. JSX, saf JavaScript 'e derleyemeyen HTML benzeri bir sözdizimidir. Örneğin:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

JavaScript 'ı zaten biliyorsanız, öğrenme tepki verme kolay olmalıdır. Neredeyse çok fazla öğrenme eğrisi veya angular veya diğer popüler kitaplıklarla ilgili özel söz dizimi yoktur.

Yanıt verme tam bir çerçeve olmadığından, genellikle diğer kitaplıkların yönlendirme, Web API çağrıları ve bağımlılık yönetimi gibi işlemleri işlemesini isteyeceksiniz. Her biri için en iyi kitaplığı seçebilirsiniz, ancak bu kararların hepsini yapmanız ve seçtiğiniz tüm kitaplıkların tümünü doğrulamanız gerektiğinde tüm bu kararları vermeniz gerekir. İyi bir başlangıç noktası isterseniz, bir dizi uyumlu kitaplığı tepki vererek, yanıt veren bir yük görüntüsü gibi bir başlatıcı kiti kullanabilirsiniz.

### <a name="choosing-a-spa-framework"></a>SPA çerçevesi seçme

Hangi JavaScript çerçevesinin, SPA 'nizi destekleyecek en iyi şekilde çalıştığını düşünürken aşağıdaki noktalara dikkat edin:

- Takımınız Framework 'ü ve bağımlılıklarını (bazı durumlarda TypeScript dahil) biliyor musunuz?

- Ne kadar kolay bir çatı çerçevesidir ve bunu yapmanın varsayılan yolunu kabul etmiş olursunuz?

- Uygulamanızın gerektirdiği tüm özellikleri (veya bir yardımcı Kitaplık) içeriyor mu?

- İyi belgelenmiş mi?

- Topluluk nasıl etkin? Yeni projeler derleme ile derlensin mi?

- Etkin olan temel ekibi nedir? Sorun çözümlenmekte ve yeni sürümler düzenli olarak sevk ediliyor mu?

JavaScript çerçeveleri Breakneck hızında gelişmeye devam eder. Daha sonra bağımlı olmaya başlayacaksınız bir çerçeve seçme riskini azaltmaya yardımcı olması için yukarıda listelenen konuları kullanın. Özellikle risk-karşıtı, ticari destek sunan ve/veya büyük bir kuruluş tarafından geliştirilen bir çerçeveyi düşünün.

> ### <a name="references--client-web-technologies"></a>Başvurular – Istemci Web teknolojileri
>
> - **HTML ve CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass ile karşılaştırması BÜYÜKTÜR**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **DAHA az, Sass ve yazı tipi harika olan uygulamaları ASP.NET Core Stillendirme**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **ASP.NET Core 'de istemci tarafı geliştirme**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **Temingshot 'e tepki verme**  
> <https://github.com/coryhouse/react-slingshot>
> - **Tepki ve açı 2 karşılaştırması**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **2017 en iyi 5 JavaScript çerçeveleri**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
>[Önceki](common-web-application-architectures.md)İleri
>[](develop-asp-net-core-mvc-apps.md)
