---
title: Geleneksel web uygulamaları ile tek sayfa uygulamaları arasında seçim yapma
description: Web uygulamaları yaparken geleneksel web uygulamaları ve tek sayfalı uygulamalar (SPA) arasında nasıl seçim yapabileceğinizi öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450114"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Geleneksel Web Uygulamaları ve Tek Sayfauygulamaları (SPA' lar) arasında seçim yapın

> "Atwood Yasası: JavaScript yazılabilir herhangi bir uygulama, sonunda JavaScript yazılacaktır."  
> _\-Jeff Atwood_

Bugün web uygulamaları oluşturmak için iki genel yaklaşım vardır: sunucuda uygulama mantığının çoğunu gerçekleştiren geleneksel web uygulamaları ve bir web tarayıcısında kullanıcı arabirimi mantığının çoğunu gerçekleştiren tek sayfalı uygulamalar (SPA'lar), öncelikle web API'leri kullanarak web sunucusu ile iletişim. Bir hibrid yaklaşım da mümkündür, daha büyük bir geleneksel web uygulaması içinde bir veya daha fazla zengin SPA benzeri alt uygulamalar barındırmak en basit olmak.

Şu anda geleneksel web uygulamalarını kullanın:

- Uygulamanızın istemci tarafı gereksinimleri basit veya salt okunur.

- Uygulamanızın JavaScript desteği olmayan tarayıcılarda çalışması gerekir.

- Ekibiniz JavaScript veya TypeScript geliştirme tekniklerini bilmiyor.

Spa'yı şu zaman kullanın:

- Uygulamanız birçok özelliğe sahip zengin bir kullanıcı arabirimini ortaya çıkarmalıdır.

- Ekibiniz JavaScript ve/veya TypeScript geliştirmesini biliyor.

- Uygulamanız, diğer (dahili veya genel) istemciler için zaten bir API sunmalıdır.

Ayrıca, SPA çerçeveleri daha fazla mimari ve güvenlik uzmanlığı gerektirir. Onlar geleneksel web uygulamaları daha sık güncellemeleri ve yeni çerçeveler nedeniyle daha fazla karmaşa deneyim. Otomatik oluşturma ve dağıtım süreçlerini yapılandırmak ve kapsayıcılar gibi dağıtım seçeneklerini kullanmak, SPA uygulamalarında geleneksel web uygulamalarına göre daha zor olabilir.

SPA yaklaşımı ile kullanıcı deneyiminde yapılan iyileştirmeler bu hususlara göre tartılmalıdır.

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 blazor denilen zengin, interaktif ve composable UI oluşturmak için yeni bir model tanıttı. Blazor sunucu tarafı geliştiricilerin sunucuda Razor ile Kullanıcı Arabirimi oluşturmasına ve bu kodun tarayıcıya teslim edilmesine ve [WebAssembly'i](https://webassembly.org/)kullanarak istemci tarafından yürütülmesine olanak tanır. Blazor sunucu tarafı core 3.0 veya daha sonra ASP.NET ile artık kullanılabilir. Blazor istemci tarafı 2020 yılında satışa sunulmalıdır.

Blazor, tamamen sunucu tarafından işlenmiş bir web uygulaması mı yoksa SPA mı oluşturulmasını değerlendirirken göz önünde bulundurması gereken yeni, üçüncü bir seçenek sunar. Önemli bir JavaScript geliştirmesi için gerek kalmadan Blazor kullanarak zengin, SPA benzeri istemci tarafı davranışları oluşturabilirsiniz. Blazor uygulamaları veri istemek veya sunucu tarafı işlemleri gerçekleştirmek için API'leri arayabilir.

Web uygulamanızı Blazor ile oluşturmayı düşünün:

- Uygulamanız zengin bir kullanıcı arabirimini ortaya çıkarmalıdır

- Ekibiniz .NET geliştirme ile JavaScript veya TypeScript geliştirmeden daha rahattır

Blazor hakkında daha fazla bilgi için bkz: [Blazor ile başlayın.](https://blazor.net/docs/get-started.html)

## <a name="when-to-choose-traditional-web-apps"></a>Geleneksel web uygulamaları ne zaman seçilir?

Aşağıda geleneksel web uygulamaları seçmek için daha önce belirtilen nedenleri daha ayrıntılı bir açıklamadır.

**Uygulamanız basit, muhtemelen salt okunur, istemci tarafı gereksinimlerine sahiptir**

Birçok web uygulamaları öncelikle kullanıcılarının büyük çoğunluğu tarafından bir okuma sadece moda tüketilir. Salt okunur (veya çoğunlukla okuma) uygulamaları, büyük bir devleti koruyan ve manipüle eden uygulamalardan çok daha basit olma eğilimindedir. Örneğin, arama motoru, metin kutusu olan tek bir giriş noktasından ve arama sonuçlarını görüntülemek için ikinci bir sayfadan oluşabilir. Anonim kullanıcılar kolayca istekte bulunabilir ve istemci tarafı mantığına çok az ihtiyaç vardır. Aynı şekilde, bir blog veya içerik yönetim sisteminin genel kullanıma yönelik uygulaması genellikle istemci tarafı olmayan içeriklerden oluşur. Bu tür uygulamalar, web sunucusunda mantık gerçekleştiren ve HTML'nin tarayıcıda görüntülenmesini sağlayan geleneksel sunucu tabanlı web uygulamaları olarak kolayca oluşturulur. Sitenin her benzersiz sayfasının arama motorları tarafından yer işaretli ve dizine eklenebilir kendi URL'si olması (varsayılan olarak, bunu uygulamanın ayrı bir özelliği olarak eklemek zorunda kalmadan) bu tür senaryolarda da açık bir avantajdır.

**Uygulamanızın JavaScript desteği olmayan tarayıcılarda çalışması gerekiyor**

Sınırlı veya hiç JavaScript desteği olmayan tarayıcılarda çalışması gereken Web uygulamaları geleneksel web uygulaması iş akışları kullanılarak yazılmalıdır (veya en azından bu tür davranışlara geri dönebilmelidir). SCA'ların çalışabilmesi için istemci tarafındaki JavaScript gerekir; mevcut değilse, SPA'lar iyi bir seçim değildir.

**Ekibiniz JavaScript veya TypeScript geliştirme tekniklerine aşina değil**

Ekibiniz JavaScript veya TypeScript'e aşina değilse, ancak sunucu tarafındaki web uygulaması geliştirmesini biliyorsa, büyük olasılıkla geleneksel bir web uygulamasını SPA'dan daha hızlı bir şekilde sunabilirler. SSPA'ları programlamayı öğrenmek bir hedef olmadığı veya SPA tarafından sağlanan kullanıcı deneyimi gerekli olmadığı sürece, geleneksel web uygulamaları bunları oluşturmaya zaten aşina olan ekipler için daha üretken bir seçimdir.

## <a name="when-to-choose-spas"></a>SP'ler ne zaman seçilir?

Aşağıda, web uygulamanız için tek sayfalı uygulamalar geliştirme stilinin ne zaman seçileceklerine ilişkin daha ayrıntılı bir açıklama yer aınızverilmiştir.

**Uygulamanız birçok özelliğe sahip zengin bir kullanıcı arabirimini ortaya çıkarmalıdır**

SP'ler, kullanıcılar işlem yaptıklarında veya uygulamanın alanları arasında gezinirken sayfanın yeniden yüklenmesi gerektirmeyen zengin istemci tarafı işlevselliğini destekleyebilir. SCA'lar arka planda veri getirerek daha hızlı yüklenebilir ve tam sayfa yeniden yüklemeleri nadir olduğundan tek tek kullanıcı eylemleri daha duyarlıdır. SCA'lar, kullanıcının form göndermek için bir düğmeyi tıklatması gerekmeden kısmen tamamlanmış formları veya belgeleri kaydederek artımlı güncelleştirmeleri destekleyebilir. SCA'lar, sürükle ve bırak gibi zengin istemci tarafı davranışlarını geleneksel uygulamalardan çok daha kolay destekleyebilir. SBA'lar bağlantısı kesilen bir modda çalışacak şekilde tasarlanabilir ve bağlantı yeniden kurulduktan sonra sunucuya yeniden eşitlenen istemci tarafındaki bir modelde güncelleştirmeler yapılabilir. Uygulamanızın gereksinimleri, tipik HTML formlarının sunduklarının ötesine giden zengin işlevselliği içeriyorsa, SPA tarzı bir uygulama seçin.

Sık sık, SP'lerin geçerli işlemi yansıtan adres çubuğunda anlamlı bir URL görüntülemek (ve kullanıcıların bu URL'ye geri dönmek için yer imi veya derin bağlantı sağlamasına izin vermek) gibi geleneksel web uygulamalarında yerleşik özellikleri uygulaması gerekir. SCA'lar ayrıca kullanıcıların tarayıcının ileri ve geri düğmelerini sürpriz yapmayacak sonuçlarla kullanmasına izin vermelidir.

**Ekibiniz JavaScript ve/veya TypeScript geliştirmesini biliyor**

SP'ler yazmak, JavaScript ve/veya TypeScript ve istemci tarafı programlama teknikleri ve kitaplıklarına aşinalık gerektirir. Ekibiniz Açısal gibi bir SPA çerçevesi kullanarak modern JavaScript yazma konusunda yetkili olmalıdır.

> ### <a name="references--spa-frameworks"></a>Referanslar – SPA Çerçeveleri
>
> - **Angular**  
>   <https://angular.io>
> - **Tepki**
>   <https://reactjs.org/>
> - **JavaScript Çerçevelerinin Karşılaştırılması**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Başvurunuz, diğer (dahili veya genel) istemciler için zaten bir API ortaya çıkarmalıdır**

Bir web API'sini zaten diğer istemciler tarafından kullanılmak üzere destekliyorsanız, bu API'lerden yararlanan bir SPA uygulaması oluşturmak için sunucu tarafındaki mantığı çoğaltmak yerine daha az çaba gerektirebilir. SP'ler, kullanıcılar uygulamayla etkileşimde bulununarak verileri sorgulamak ve güncellemek için web API'lerini kapsamlı bir şekilde kullanır.

## <a name="when-to-choose-blazor"></a>Blazor ne zaman seçilir?

Aşağıda web uygulamanız için Blazor'u ne zaman seçeceğiniz hakkında daha ayrıntılı bir açıklama yer aınızvededi.

**Uygulamanız zengin bir kullanıcı arabirimini ortaya çıkarmalıdır**

JavaScript tabanlı SCA'lar gibi Blazor uygulamaları da sayfa yeniden yüklemesi olmadan zengin istemci davranışını destekleyebilir. Bu uygulamalar kullanıcılara daha duyarlıdır ve belirli bir kullanıcı etkileşimine yanıt vermek için yalnızca gereken verileri (veya HTML)'yi getirir. Düzgün tasarlanmış, sunucu tarafı Blazor uygulamaları bu özellik desteklendikten sonra en az değişiklik ile istemci tarafı Blazor uygulamaları olarak çalışacak şekilde yapılandırılabilir.

**Ekibiniz .NET geliştirme ile JavaScript veya TypeScript geliştirmeden daha rahattır**

Birçok geliştirici .NET ve Razor ile JavaScript veya TypeScript gibi istemci tarafındaki dillerden daha üretkendir. Uygulamanın sunucu tarafı zaten .NET ile geliştirilmekte olduğundan, Blazor'un kullanılması takımdaki her .NET geliştiricisinin uygulamanın ön ucunun davranışını anlamasını ve oluşturmasını sağlar.

## <a name="decision-table"></a>Karar tablosu

Aşağıdaki karar tablosu, geleneksel bir web uygulaması, SPA veya Blazor uygulaması arasında seçim yaparken göz önünde bulundurulması gereken temel faktörlerden bazılarını özetlemektedir.

| **Faktörü**                                           | **Geleneksel Web Uygulaması** | **Tek Sayfa Uygulaması** | **Blazor Uygulaması**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| JavaScript/TypeScript ile Gerekli Takım Aşinalığı | **En az**             | **Gerekli**                | **En az**     |
| Komut Dosyası Olmadan Tarayıcıları Destekleyin                   | **Desteklenen**           | **Desteklenmiyor**           | **Desteklenen**   |
| En Az İstemci Tarafı Uygulama Davranışı             | **Uygun**         | **Overkill**                | **Uygun**      |
| Zengin, Karmaşık Kullanıcı Arabirimi Gereksinimleri            | **Sınırlı**             | **Uygun**             | **Uygun** |

>[!div class="step-by-step"]
>[Önceki](modern-web-applications-characteristics.md)
>[Sonraki](architectural-principles.md)
