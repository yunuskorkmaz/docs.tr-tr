---
title: Ortak istemci tarafı web teknolojileri
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Ortak istemci tarafı web teknolojileri
author: ardalis
ms.author: wiwagn
ms.date: 6/28/2018
ms.openlocfilehash: eb5612e0cbdc52e397ba367b4cc744796174d06c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153897"
---
# <a name="common-client-side-web-technologies"></a>Ortak istemci tarafı web teknolojileri

> "Web siteleri içeriden iyi arayın ve çıkış."  
> _-Paul Cookson_

ASP.NET Core web uygulamaları uygulamalardır ve bunlar genellikle HTML, CSS ve JavaScript gibi istemci tarafı web teknolojileri dayanır. Powerapps'in düzen ve stil (CSS) ve (JavaScript) aracılığıyla davranışını sayfa (HTML) içeriği ayırarak, karmaşık web apps ayrımı ile ilgili sorunlar, ilkeye yararlanabilirsiniz. Bu sorunlar değil birbirine zaman yapısı, tasarım ve uygulama davranışını ileride yapılacak değişiklikler kolayca daha fazla yapılamaz.

HTML ve CSS göreceli olarak kararlı olan uygulama çerçeveleri ile JavaScript ve yardımcı programları geliştiriciler web tabanlı uygulamalar oluşturmak için çalışmak olsa da, breakneck hızında geliştirilmektedir. Bu bölümde, JavaScript web geliştiricilerin Angular ve React istemci tarafı kitaplıklarını üst düzey bir genel bakış sağladığı gibi uygulama geliştirmenin bir parçası olarak kullanılan birkaç şekilde bakar.

## <a name="html"></a>HTML

HTML (HyperText Markup Language), web sayfaları ve web uygulamaları oluşturmak için kullanılan standart bir biçimlendirme dilidir. Biçimlendirilmiş metin, resimler, form girişleri ve diğer yapıları temsil eden sayfaların yapı taşları öğeleri oluşturur. Bir tarayıcı bir sayfası veya uygulama getirilirken olup olmadığını bir URL'ye yapılır; bir istek gönderir yani ilk şey döndürülen HTML belgesi olur. Bu HTML belgesi, başvuru veya kendi Görünüm ve düzeni hakkında daha fazla bilgi, CSS ve JavaScript biçiminde davranış biçimindedir dahil.

## <a name="css"></a>CSS

CSS (geçişli stil sayfaları), Görünüm ve HTML öğeleri yerleşimini denetlemek için kullanılır. CSS stilleri doğrudan HTML öğesiyle uygulanan, ayrı olarak aynı sayfada tanımlı veya ayrı bir dosyada tanımlanabilir ve sayfa tarafından başvurulan. Stilleri cascade nasıl bunlar belirli bir HTML öğesini seçmek için kullanıldığına bağlı. Örneğin, bir stil belgenin tamamına uygulayabilirsiniz, ancak belirli bir öğeye uygulanan stil tarafından üzerine yazılırdı. Benzer şekilde, bir öğe özgü stil, o öğenin (kimliğini) aracılığıyla belirli bir örneğini hedefleyen bir stili tarafından sırayla yazılırdı öğeye uygulanan bir CSS sınıfı uygulanan stil tarafından yazılırdı. Şekil 6-1

**Şekil 6-1.** Sırayla CSS Belirginliğe kuralları.

![](./media/image6-1.png)

Kendi ayrı bir stil sayfası dosyalarında stilleri tutmak ve seçim tabanlı geçişli uygulama içinde tutarlı ve yeniden kullanılabilir stilleri uygulamak için kullanmak en iyisidir. HTML stil kuralların yerleştirme kaçınılmalıdır ve belirli ayrı ayrı öğeler (tüm sınıflar öğeleri veya belirli bir CSS sınıfı uygulanmış olan öğe yerine) stilleri uygulamak kural özel durumu olmalıdır.

### <a name="css-preprocessors"></a>CSS önişlemcilerini

CSS stil sayfaları, koşullu mantık, değişkenler ve diğer programlama dili özelliklerini desteği yoksundur. Bu nedenle, büyük stil sayfaları, genellikle aynı renk, yazı tipi veya diğer ayar HTML öğelerinin ve CSS sınıfları birçok farklı çeşitleri için uygulanan gibi çok sayıda yineleme, içerir. CSS önişlemcilerini izleyin, stil sayfaları yardımcı [KURU İlkesi](https://deviq.com/don-t-repeat-yourself/) değişkenleri ve mantıksal için destek ekleyerek.

En popüler CSS önişlemcilerini Sass ve daha az olan. Her ikisi de CSS genişletmek ve düz bir CSS dosyası geçerli bir Sass ya da daha az dosya yani geriye dönük olarak, ile uyumludur. Sass Ruby tabanlıdır ve JavaScript tabanlı küçük ve her ikisi de genellikle yerel geliştirme sürecinizin bir parçası olarak çalışır. Komut satırı araçları Visual Studio'da kullanılabilir yanı sıra yerleşik desteği çalıştırmak için sahip Gulp veya Grunt görevlerini kullanarak.

## <a name="javascript"></a>JavaScript

JavaScript, ECMAScript dil belirtimi standartlaştırılmış bir dinamik, yorumlanan programlama dilidir. Web programlama dilidir. CSS gibi JavaScript gibi öznitelikleri HTML öğeleri içinde bir sayfada veya ayrı dosyalarda komut dosyası blokları olarak tanımlanabilir. Yalnızca CSS gibi genellikle JavaScript ayrı dosyalar halinde düzenlemek için ayrılmış bağımsız web sayfaları veya uygulama görünümleri bulunan HTML mümkün olduğunca tutulması önerilir.

JavaScript ile web uygulamanızda çalışırken yaygın olarak gerçekleştirmek için gereken birkaç görev vardır:

- Bir HTML öğesini seçerek ve alınıyor ve/veya değeri güncelleştiriliyor.

- Web API'si veri için Sorgulanıyor.

- Bir Web API (ve sonuç ile bir geri çağırma yanıt) için bir komut gönderme.

- Doğrulama gerçekleştiriliyor.

Tüm JavaScript tek başına bu görevleri gerçekleştirebilir, ancak bu görevleri kolaylaştırmak için birçok mevcut. İlk ve en başarılı bu kitaplıkları web sayfalarında bu görevleri basitleştirmek için popüler bir seçim olmaya devam jQuery, biridir. Tek sayfa uygulamaları için (Spa'lar), jQuery, Angular ve React sunmak istediğiniz özelliklerin çoğunu sağlamaz.

### <a name="legacy-web-apps-with-jquery"></a>JQuery ile eski web uygulamaları

Antik JavaScript çerçevesi standartlarında rağmen jQuery, HTML/CSS ile çalışma ve web API AJAX çağrıları yapan uygulamalar oluşturmak için çok yaygın kullanılan bir kitaplık olmaya devam eder. Ancak, jQuery tarayıcı belge nesne modeli (DOM) düzeyinde çalışır ve varsayılan olarak yalnızca bir kesinlik temelli yerine bildirim temelli, modeli sunar.

Örneğin, bir metin kutusunun değerini 10 aşarsa, sayfadaki bir öğeyi görünür yapılması gerektiğini düşünün. JQuery bu genellikle bir olay işleyicisi ile metin kutusunun değerini inceleyin ve bu değeri temel alarak hedef öğenin görünürlüğünü ayarlayabilirsiniz kod yazarak uygulanması. Kesinlik temelli, kod tabanlı bir yaklaşım budur. Başka bir framework, veri bağlama öğesi görünürlüğünü metin kutusunun değerini bildirimli olarak bağlamak için bunun yerine kullanabilirsiniz. Bu, herhangi bir kod yazmaya gerek duymaz ancak bunun yerine yalnızca veri bağlama özniteliklerle ilgili öğeleri dekorasyon gerektirir. İstemci tarafı davranışlarını daha karmaşık büyüdükçe, veri bağlama daha az kod ve koşullu karmaşıklığı daha basit çözümleriyle sonucunda sık yaklaşıyor.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs SPA Framework

| **faktörü** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| DOM soyutlar | **Evet** | **Evet** |
| AJAX desteği | **Evet** | **Evet** |
| Bildirim temelli veriler bağlama | **Yok** | **Evet** |
| MVC stili yönlendirme | **Yok** | **Evet** |
| Şablon oluşturma | **Yok** | **Evet** |
| Ayrıntılı bağlantı Yönlendirme | **Yok** | **Evet** |

JQuery doğası gereği eksik özelliklerin çoğunu diğer kitaplıkları'nın eklenmesiyle eklenebilir. Ancak, tüm bunları başından itibaren aklınızda tasarlanmış olduğundan bir SPA çerçeve Angular gibi bu özellikleri daha tümleşik bir biçimde sunar. Ayrıca, jQuery, jQuery ile herhangi bir şey yapmak için jQuery işlevleri çağırmak gerektiği anlamına gelir, bir çok kesinlik temelli kitaplığı vardır. SPA çerçeveleri sağlayan işlevselliği ve iş çoğunu, yazılacak gerçek kod gerektiren bildirimli olarak, yapılabilir.

Veri bağlama, bu harika bir örnektir. JQuery genellikle yalnızca tek satırlık bir kod DOM öğesinin değeri almaya veya bir öğenin değerini ayarlamak için alır. Ancak, dilediğiniz zaman öğenin değerini değiştirmeniz gerekir ve bazen bir sayfada birden çok işlevlerde meydana gelir Bu kod yazmak zorundasınız. Başka bir ortak öğe görünürlük örnektir. JQuery içinde denetimine belirli öğeleri görünür olup olmadığını kod burada yazmalısınız pek çok farklı yerde olabilir. Her veri bağlamayı kullanırken bu gibi durumlarda, kod yazılması gerekir. Yalnızca değeri veya öğeyi/öğeleri için söz konusu görünürlüğünü bağlama bir *viewmodel* sayfasında ve o değişiklikleri viewmodel otomatik olarak ilişkili öğeleri yansıtılır.

### <a name="angular-spas"></a>Angular Spa'lar

AngularJS dünyanın en popüler JavaScript altyapılarından birini hızlı hale geldi. Angular 2 ile takım yukarı framework baştan yeniden (kullanarak [TypeScript](https://www.typescriptlang.org/)) ve AngularJS Angular yalnızca yeni marka adları verilmiştir. Şu anda 4 sürümünde Angular tek sayfa uygulamaları oluşturmaya yönelik güçlü bir çerçeve olmaya devam eder.

Angular uygulamalar bileşenlerini oluşturulur. Bileşenler, HTML şablonları ile özel nesneleri birleştirerek ve sayfasının bir bölümü denetleyebilirsiniz. Angular belgeleri basit bir bileşenden aşağıda gösterilmiştir:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Bileşenleri kullanılarak tanımlanır @Component bileşen hakkındaki meta verileri alır dekoratör işlevine. Seçici özelliği sayfasında bu bileşen nerede görüntülenecek öğesinin kimliği tanımlar. Şablon özelliği son satırında tanımlanan bileşenin adı özelliğine karşılık gelen bir yer tutucu içeren basit bir HTML şablonudur.

Bileşenleri ve DOM öğeleri yerine şablonları ile çalışarak daha yüksek düzeyde soyutlama ve yalnızca JavaScript ("vanilla JS" olarak da bilinir) kullanılarak yazılmış uygulamalar genel daha az kod veya jQuery ile Angular uygulamalarından çalışabilir. Angular Ayrıca, istemci tarafı betiklerinin nasıl düzenlediğiniz bazı kararnamesi'nin uygular. Kural gereği, Angular uygulamalarından ile bir uygulama klasöründe bulunan modülü ve bileşen komut dosyalarını ortak bir klasör yapısı kullanın. Angular komut dosyaları oluşturma, dağıtma ve uygulamayı genellikle üst düzey bir klasörde bulunan test ile ilgili.

Angular da harika kullanım araçlarının komut satırı arabirimi (CLI) sağlar. (Zaten git ve npm yüklü olduğu varsayılarak) Angular ile geliştirme yerel olarak Başlarken oluşur GitHub ve çalışan bir depo yalnızca kopyalama `npm install` ve `npm start`. Bunun üzerindeki kullanımlar Angular projeleri oluşturma, dosyaları ekleyin ve test, paketleme ve dağıtım görevleri yardımcı kendi CLI aracını birlikte gelir. Bu CLI kullanım tooling Angular özellikle de harika CLI destekleyen özellikleri ASP.NET Core ile uyumlu hale getirir.

Microsoft bir başvuru uygulaması geliştirmiştir [hizmetine](https://aka.ms/MicroservicesArchitecture), Angular SPA uygulamasını içerir. Bu uygulama, çevrimiçi mağaza kataloğuyla sepet, yükleme ve görüntüleme öğelerinden alışveriş ve sipariş oluşturma işleme yönetmek için Angular modüller içerir. Görüntüleyebilir ve örnek uygulamayı indirin [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>react

Angular sunan tam bir Model-View-Controller deseni uygulaması, React ile görünümleri yalnızca ilgilenir. Bir SPA oluşturmak için ek kitaplıklar yararlanarak gerekecek bir çerçeve, yalnızca bir kitaplık değil.

React'ın en önemli özelliklerden biri, sanal bir DOM kullanımıdır Sanal DOM React (sanal DOM gerçek DOM hangi bölümlerinin güncelleştirilmesi gereken iyileştirebilirsiniz) performans ve Test Edilebilirlik (React ve etkileşimlerini kendi sanal DOM ile test etmek için bir tarayıcı gerek yoktur) dahil olmak üzere çeşitli avantajlar sağlar.

React ile HTML nasıl çalıştığına olağandışıdır. React katı bir ayrım kodu ve biçimlendirmeyi (başvuruları ile JavaScript HTML özniteliklerinde belki de görünmesini), arasında olması yerine doğrudan HTML, JavaScript kod JSX ekler. JSX aşağı saf JavaScript derleyebilirsiniz HTML benzeri sözdizimi aşağıdaki gibidir. Örneğin:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

JavaScript zaten biliyorsanız, React öğrenme kolay olmalıdır. Hiç neredeyse çok fazla öğrenme eğrisi veya özel bir sözdizimi olarak Angular veya diğer popüler kitaplıkları ile ilgili.

Framework'ün tamamını React olmadığı için genellikle diğer kitaplıkları yönlendirme gibi şeyleri işlemek için web API çağrıları ve bağımlılık Yönetimi istersiniz. Güzel bir şey olduğunu, bunların her biri için en uygun kitaplığı seçebilirsiniz, ancak olumsuz bu kararlar sağlayın ve işiniz bittiğinde tüm seçilen kitaplıklara birlikte düzgün çalışacak doğrulamak ihtiyacınız olan. İyi bir başlangıç noktası istiyorsanız, bir başlangıç Seti uyumlu kitaplıkların React ile birlikte bir dizi prepackages React Slingshot gibi kullanabilirsiniz.

### <a name="choosing-a-spa-framework"></a>SPA Framework seçme

Hangi JavaScript çerçevesini dikkate en iyi, SPA desteklemek için çalışır, aşağıdaki konuları göz önünde bulundurun:

- Takımınız framework ve bağımlılıklarını (bazı durumlarda dahil olmak üzere TypeScript) hakkında bilgi sahibi mi?

- Nasıl kendine özgü tarzı olan bir çerçevesidir ve bunu yapmak, varsayılan yolu kabul?

- Uygulamanız için gerekli tüm özelliklere (veya bir yardımcı kitaplık) içeriyor mu?

- Bu, iyi belgelendirilmiş mi?

- Kendi topluluk nasıl etkin mi? Yeni projeler oluşturma ile oluşturulur?

- Kendi çekirdek ekibi nasıl etkin mi? Çözümlenen ve yeni sürümleri olan sorunları düzenli olarak gönderilir?

Yeni JavaScript çerçevesi breakneck hızıyla iyileşmeye devam etmektedir. Bağımlı olan daha sonra vazgeç bir çerçeve seçme riskini azaltmaya yardımcı olmak için yukarıda listelenen konularını kullanın. Özellikle başarılarında, ticari destek sağlar ve/veya büyük bir kuruluş tarafından geliştirilen bir çerçeve göz önünde bulundurun.

> ### <a name="references--client-web-technologies"></a>Başvuruları – istemci Web teknolojileri
> - **HTML ve CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. DAHA AZ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **ASP.NET Core uygulamaları daha az, Sass ve Font Awesome stil oluşturma**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **ASP.NET core'da istemci tarafı geliştirme**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **React Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **React vs Angular 2 karşılaştırma**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **2017'in en iyi 5 JavaScript çerçevesi**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
>[Önceki](common-web-application-architectures.md)
>[İleri](develop-asp-net-core-mvc-apps.md)