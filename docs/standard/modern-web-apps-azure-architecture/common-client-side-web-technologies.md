---
title: "Ortak istemci tarafı web teknolojileri"
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | Ortak istemci tarafı web teknolojileri"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e8e156552fd4aa733594c01845fb7ed1643b4aef
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="common-client-side-web-technologies"></a>Ortak istemci tarafı Web teknolojileri

> "Web siteleri içeriden iyi arayın ve çıkış."  
> _-Paul Cookson_

## <a name="summary"></a>Özet

Web uygulamaları ASP.NET Core uygulamaları olan ve genellikle HTML, CSS ve JavaScript gibi istemci tarafı web teknolojileri güvenirler. Karmaşık web uygulamaları, Düzen ve stil (CSS) ve davranışını (JavaScript) aracılığıyla (HTML) sayfasının içeriği ayırarak ayrımı biri ile ilgili sorunlar ilkesini yararlanabilirsiniz. Bu sorunları değil birbirine zaman yapısı, tasarım veya uygulamanın davranışını ileride yapılacak değişiklikler kolayca daha fazla yapılamaz.

HTML ve CSS görece kararlı, JavaScript, uygulama çerçeveleri yoluyla ve yardımcı programları geliştiricilerin web tabanlı uygulamalar oluşturmak için çalışmak olsa da, breakneck hızda gelişen. Bu bölümde JavaScript parçası olarak Angular ve tepki istemci tarafı kitaplıkları üst düzey bir genel bakış sağlar gibi uygulamaları geliştirme, web geliştiricileri tarafından kullanılan birkaç şekilde bakar.

## <a name="html"></a>HTML

HTML (HyperText Markup Language), web sayfaları ve web uygulamaları oluşturmak için kullanılan standart biçimlendirme dilidir. Öğeleri biçimlendirilmiş metin, görüntüler, form girişleri ve diğer yapıları temsil eden sayfaların yapı taşlarını oluşturur. Bir tarayıcı bir URL için bir sayfaya veya uygulamanın getirme olup olmadığını istekte bulunduğunda, ilk şey diğer bir deyişle döndürülen HTML belgesi değil. Bu HTML belgesi başvuru veya CSS ve JavaScript biçiminde davranış biçiminde kendi Görünüm ve düzeni hakkında ek bilgi içerir.

## <a name="css"></a>CSS

CSS (geçişli stil sayfaları), Görünüm ve HTML öğeleri yerleşimini denetlemek için kullanılır. CSS stilleri doğrudan bir HTML öğesi uygulanan, ayrı ayrı aynı sayfada tanımlı veya ayrı bir dosyaya tanımlanabilir ve sayfa tarafından başvurulan. Stilleri cascade nasıl bunlar belirli bir HTML öğesini seçmek için kullanıldığına bağlı. Örneğin, bir stil belgenin tamamına geçerli, ancak belirli bir öğeye uygulanan stil geçersiz. Benzer şekilde, bir öğenin özgü stili o öğeye (aracılığıyla kimliğini) belirli bir örneği hedefleyen bir stil sırayla geçersiz öğesi uygulandığı bir CSS sınıfı uygulanan stil geçersiz. Şekil 6-1

**Şekil 6-1.** CSS Belirginliğe kuralları, sırayla.

![](./media/image6-1.png)

Kendi ayrı stil sayfası dosyalarında stilleri tutmak ve uygulama içinde tutarlı ve yeniden kullanılabilir stilleri uygulamak için seçim tabanlı basamaklı'ı kullanmak için en iyisidir. Stil kurallarını HTML içinde yerleştirme kaçınılmalıdır ve belirli ayrı ayrı öğeler (tüm sınıflar öğeleri veya uygulanmış belirli bir CSS sınıfı beklendiğinden öğelerin yerine) stilleri uygulamak özel durum kuralı olması gerekir.

### <a name="css-preprocessors"></a>CSS Önişlemcilerini

CSS stil sayfaları koşullu mantık, değişkenlerin ve diğer programlama dili özellikleri desteği. Bu nedenle, aynı renk, yazı tipi veya diğer ayarlar için birçok farklı değişkenleri HTML öğeleri ve CSS sınıfları, uygulanan gibi büyük stil sayfaları çok fazla yineleme, genellikle içerir. CSS önişlemcilerini izleyin, stil sayfaları yardımcı [KURU ilkesine](http://deviq.com/don-t-repeat-yourself/) değişkenleri ve mantığı için destek ekleyerek düzenleyin.

En popüler CSS önişlemcilerini Sass ve daha az ' dir. Her ikisi de CSS genişletmek ve düz bir CSS dosyası geçerli bir Sass veya daha az dosya yani geriye dönük olarak, ile uyumludur. Sass Ruby dayalıdır ve JavaScript tabanlı küçük ve her ikisi de genellikle yerel geliştirme işleminizin bir parçası olarak çalışır. Her ikisi de komut satırı çalıştırmak için Visual Studio'da kullanılabilir yanı sıra yerleşik destek araçları sahip Gulp veya Grunt görevler kullanma.

## <a name="javascript"></a>JavaScript

JavaScript, ECMAScript dil belirtiminde standartlaştırılmış bir dinamik, yorumlanan programlama dilidir. Bu Web programlama dilidir. CSS gibi JavaScript olarak HTML öğeleri özniteliklerle bir sayfanın içinde veya ayrı dosyalarda komut dosyası blokları olarak tanımlanabilir. Yalnızca CSS gibi genellikle ayrı dosyalara JavaScript düzenlemek için ayrılmış web sayfalarını ayrı ayrı veya uygulama görünümleri bulunan HTML gelen mümkün olduğunca tutulması önerilir.

Web uygulamanızda JavaScript ile çalışırken, yaygın olarak gerçekleştirmek için gereken birkaç görev vardır:

-   Bir HTML öğesini seçerek ve alma ve/veya değeri güncelleştiriliyor

-   Bir Web API veri sorgulama

-   Bir Web API için bir komut gönderme (ve bir geri arama sonucu ile yanıt verme)

-   Doğrulama gerçekleştirme

Tüm JavaScript tek başına bu görevleri gerçekleştirebilir, ancak bu görevleri kolaylaştırmak için birçok kitaplıkları mevcut. İlk ve bu kitaplıkları'nın en başarılı web sayfalarında bu görevleri basitleştirmek için popüler bir seçimdir olmaya devam jQuery biridir. Tek sayfa uygulamaları için (SPAs), jQuery Angular ve tepki sunmak istediğiniz özelliklerin çoğunu sağlamaz.

### <a name="legacy-web-apps-with-jquery"></a>JQuery ile eski Web uygulamaları

Eski JavaScript framework standartları tarafından rağmen jQuery HTML/CSS ile çalışma ve web API'leri için AJAX çağrıları yapma uygulamaları oluşturmak için çok sık kullanılan bir kitaplık olmaya devam ediyor. Ancak, jQuery tarayıcı belge nesne modeli (DOM) düzeyinde çalışır ve varsayılan olarak yalnızca bir kesinlik temelli yerine bildirim temelli, modeli sunar.

Örneğin, 10 textbox's değeri aşarsa, bir öğeyi sayfada görünür yapılması gerektiğini düşünün. JQuery içinde bu genellikle bir olay işleyicisi textbox ait değer inceleyin ve bu değere göre hedef öğe görünürlüğünü ayarlayabilirsiniz koduyla yazarak uygulanması. Bu kesinlik temelli, kod tabanlı bir yaklaşımdır. Başka bir framework, bunun yerine öğenin görünürlüğü textbox değerine bildirimli olarak bağlamak veri bağlamasını kullanabilir. Bu herhangi bir kod yazmadan gerektirmez, ancak bunun yerine yalnızca veri bağlama özniteliklerle ilgili öğeleri dekorasyon gerektirir. İstemci tarafı davranışları daha karmaşık arttıkça, veri bağlama daha az kod ve koşullu karmaşıklık daha basit çözümleriyle sonucu sık yaklaşıyor.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs SPA çerçevesi

| **Faktörü** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| DOM soyutlar | **Evet** | **Evet** |
| AJAX desteği | **Evet** | **Evet** |
| Bildirim temelli veri bağlama | **Yok** | **Evet** |
| MVC stili yönlendirme | **Yok** | **Evet** |
| Şablon oluşturma | **Yok** | **Evet** |
| Ayrıntılı bağlantı Yönlendirme | **Yok** | **Evet** |

JQuery doğası gereği eksik özelliklerin çoğunu diğer kitaplıkları eklenmesiyle eklenebilir. Ancak, bunu, tümünü başından aklınızda tasarlandığından SPA framework Angular gibi bu özellikleri daha tümleşik bir şekilde sağlar. Ayrıca, jQuery jQuery ile bir şey yapmanız için jQuery işlevleri çağırmak ihtiyacınız anlamı çok kesinlik temelli bir kitaplığı vardır. SPA çerçeveleri sağlayan işlevselliği ve iş çoğunu, yazılacak gerçek bir kod gerektiren bildirimli olarak, yapılabilir.

Veri bağlama, bu harika bir örnektir. JQuery içinde genellikle yalnızca tek bir çizgi kod DOM öğesinin değerini almak veya bir öğenin değerini ayarlamak için alır. Ancak, dilediğiniz zaman öğenin değerini değiştirmeniz gerekir ve bazı durumlarda bu sayfadaki birden çok işlevlerinde meydana gelir Bu kod yazmak zorunda. Başka bir ortak öğesi görünürlük örnektir. JQuery içinde denetimine belirli öğeleri görünür olup olmadığını kodu nereye yazarsınız pek çok farklı yerde olabilir. Yazılacak olan her veri bağlamayı kullanırken, bu durumda, hiçbir kod gerekir. Yalnızca değeri veya söz konusu eleman görünürlüğünü bağlayın bir *viewmodel* sayfa ve o değişiklikleri viewmodel otomatik olarak ilişkili öğeleri yansıtılmasını.

### <a name="angular-spas"></a>Açısal SPAs

AngularJS hızlı bir şekilde bir dünyanın en popüler JavaScript uygulamayı hale geldi. Açısal 2, takım yukarı framework sıfırdan yeniden (kullanarak [TypeScript](https://www.typescriptlang.org/)) ve AngularJS Açısal yalnızca rebranded. Şu anda sürüm 4, Angular tek sayfa uygulamaları oluşturmak için sağlam bir çerçeve olmaya devam ediyor.

Açısal uygulamaları bileşenlerini oluşturulur. Bileşenleri HTML şablonları özel nesneler ile birleştirin ve sayfa bölümünü denetleyin. Angular'ın belgeleri basit bir bileşenden burada gösterilir:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Bileşenleri kullanılarak tanımlanır @Component bileşen hakkındaki meta verileri alır oluşturma öğesi işlevi. Seçici özelliği bu bileşenin görüntülenir burada sayfadaki öğenin kimliği tanımlar. Şablon özelliği son satırında tanımlanmış bileşenin name özelliğine karşılık gelen bir yer tutucu içeren basit bir HTML şablonudur.

Bileşenleri ve DOM öğeleri yerine şablonları ile çalışarak Açısal uygulamaları daha yüksek düzeyde soyutlama ve yalnızca ("vanilla JS" olarak da bilinir) JavaScript kullanılarak yazılmış uygulamalar daha az genel kod veya jQuery ile çalışır. Açısal ayrıca bazı siparişte istemci tarafı komut dosyalarınızı nasıl organize uygular. Kurala göre Açısal uygulamaları uygulama klasöründe bulunan modülü ve bileşen komut dosyalarını ortak bir klasör yapısı kullanın. Derleme, dağıtma ve uygulama genellikle daha üst düzey bir klasörde bulunan test ilgilenen Açısal betikler.

Açısal ayrıca harika kullanımını komut satırı arabirimi (CLI) araçları sağlar. (Zaten git ve npm yüklü olduğu varsayılarak) Açısal geliştirme ile yerel olarak Başlarken oluşur yalnızca GitHub ve çalışan bir depoyu kopyalama \`npm yükleme\` ve \`npm başlangıç\`. Bunun ötesinde Angular projeleri oluşturma, dosyaları ekleyin ve test etme, paketleme ve dağıtım görevleri ile yardımcı kendi CLI araç birlikte gelir. Friendliness tooling bu CLI Angular özellikle de harika CLI destek özellikleri ASP.NET Core ile uyumlu olmasını sağlar.

Microsoft bir başvuru uygulaması geliştirmiştir [eShopOnContainers](http://aka.ms/MicroservicesArchitecture), Açısal SPA uygulaması içerir. Bu uygulamayı çevrimiçi mağaza alışveriş sepeti, yükleme ve görüntü öğeleri, Kataloğu'ndan ve sırayı oluşturma işleme yönetmek için Açısal modüller içerir. Görüntüleyebilir ve örnek uygulamayı indirin [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>tepki

Angular farklı olarak, hangi sunar tam bir Model-View-Controller desen uygulaması, tepki görünümlerle yalnızca ilgilenir. Bir SPA oluşturmak için ek kitaplıklara yararlanan gerekecek framework, yalnızca bir kitaplık değil.

Sanal bir DOM kullanımı tepki'nın en önemli özelliklerden biridir Sanal DOM tepki (sanal DOM gerçek DOM hangi kısımlarının güncelleştirilmesi gereken en iyi duruma getirebilirsiniz) performans ve Test Edilebilirlik (tepki ve kendi sanal DOM ile etkileşimlerini test etmek için bir tarayıcı gerek yoktur) dahil birkaç avantaj sunar.

Tepki de HTML ile nasıl çalıştığı olağandışıdır. Tepki kod ve biçimlendirme (başvurularıyla HTML özniteliklerinin belki de görünmesini JavaScript için), arasında sıkı bir ayrım sahip olmak yerine doğrudan HTML, JavaScript kodunu içinde JSX ekler. JSX aşağıya doğru saf JavaScript derleyebilirsiniz HTML benzeri sözdizimi aşağıdaki gibidir. Örneğin:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

JavaScript zaten biliyorsanız, tepki öğrenme kolay olmalıdır. Hiç neredeyse kadar öğrenme eğrisi veya özel sözdizimi olarak Angular veya diğer popüler kitaplıkları ile ilgili.

Tepki tam framework olmadığından yönlendirme gibi şeyler işlemek için web API çağrıları ve bağımlılık yönetimi diğer kitaplıkları genellikle isteyeceksiniz. İyi şeydir, bunların her biri için en uygun kitaplığı seçebilirsiniz, ancak bu kararlar sağlayın ve tamamladığınızda tüm seçilen kitaplıklarınızın iyi birlikte çalışır. doğrulamak gereken olumsuz olan. İyi bir başlangıç noktası istiyorsanız, bir dizi uyumlu tepki birlikte prepackages tepki Slingshot gibi starter kit kullanabilirsiniz.

### <a name="choosing-a-spa-framework"></a>Bir SPA Framework'ü seçme

Hangi JavaScript çerçevesini dikkate en iyi, SPA desteklemek için ne zaman, aşağıdaki noktaları göz önünde bulundurun:

-   Ekibinizin framework ve bağımlılıklarını (bazı durumlarda dahil olmak üzere TypeScript) aşina mi?

-   Çerçeve nasıl opinionated olan ve, işlemler, varsayılan yolu kabul?

-   Bunu (veya bir yardımcı kitaplık) tüm uygulamanızı gerektiren özellikler içeriyor mu?

-   İyi belgelenmiş mi?

-   Kendi topluluk nasıl etkin mi? Yeni projeler oluşturma ile oluşturulur?

-   Çekirdek takım nasıl etkin mi? Çözümlenmiş ve yeni sürümleri olan sorunları düzenli aralıklarla gönderilir?

JavaScript çerçeveler breakneck hızıyla gelişmeye devam edin. Bağımlı olan daha sonra vazgeç framework seçme riskini azaltmaya yardımcı olmak için yukarıda listelenen konularını kullanın. Özellikle risk averse ticari destek sağlar ve/veya büyük bir kuruluş tarafından geliştirilen bir çerçeve göz önünde bulundurun.

> ### <a name="references--client-web-technologies"></a>Başvuruları – istemci Web teknolojileri
> - **HTML ve CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. DAHA AZ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **ASP.NET Core uygulamaları ile küçük, Sass ve yazı tipi harika stil oluşturma**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **ASP.NET Core istemci-tarafı geliştirme**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **tepki**  
> <https://facebook.github.io/react/>
> - **Slingshot tepki**  
> <https://github.com/coryhouse/react-slingshot>
> - **VS Açısal 2 karşılaştırma tepki**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **2017 en iyi 5 JavaScript çerçeveleri**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[Önceki] (ortak-web-uygulama-architectures.md) [sonraki] (develop-asp-net-core-mvc-apps.md)
