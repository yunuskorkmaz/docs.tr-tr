---
title: Geleneksel web uygulamaları ile tek sayfa uygulamaları arasında seçim yapma
description: Web uygulamaları oluştururken geleneksel web uygulamaları ve tek sayfalı uygulamalar (maça 'Lar) arasından seçim yapmayı öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d68c167dce791a31eeb5ca5729b50ec22c64f9b0
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331599"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Geleneksel Web Apps ve tek sayfalı uygulamalar (maça 'Lar) arasında seçim yapın

> "Atwood 'ın yasaları: JavaScript 'te yazılabilen tüm uygulamalar, sonunda JavaScript 'e yazılır. "  
> _\-Jeff Atwood_

Günümüzde web uygulamaları oluşturmaya yönelik iki genel yaklaşım vardır: sunucuda uygulama mantığının çoğunu gerçekleştiren geleneksel web uygulamaları ve bir Web tarayıcısında Kullanıcı arabirimi mantığının çoğunu gerçekleştiren tek sayfalı uygulamalar (maça 'Lar) Web API 'Leri kullanarak Web sunucusuyla iletişim kurma. Karma yaklaşım da olasıdır, en basit, daha büyük bir geleneksel Web uygulaması içinde bir veya daha fazla zengin SPA benzeri alt uygulama barındırmakta.

Şu durumlarda geleneksel web uygulamaları kullanmanız gerekir:

- Uygulamanızın istemci tarafı gereksinimleri basit veya hatta salt okunurdur.

- Uygulamanızın JavaScript desteği olmayan tarayıcılarda çalışması gerekir.

- Takımınız JavaScript veya TypeScript geliştirme tekniklerini tanımıyor.

Şu durumlarda SPA kullanmanız gerekir:

- Uygulamanız çok sayıda özelliği olan zengin bir kullanıcı arabirimi kullanıma sunmalıdır.

- Takımınız JavaScript ve/veya TypeScript geliştirmeyi biliyor.

- Uygulamanız zaten diğer (iç veya genel) istemciler için bir API 'YI kullanıma sunmalıdır.

Ayrıca, SPA çerçeveleri daha fazla mimari ve güvenlik uzmanlığı gerektirir. Geleneksel Web uygulamalarından daha sık güncelleştirmeler ve yeni çerçeveler nedeniyle daha fazla karmaşıklık yaşar. Otomatik derleme ve dağıtım süreçlerini yapılandırma ve kapsayıcılar gibi dağıtım seçeneklerinin kullanılmasıyla geleneksel Web uygulamalarından daha fazla SPA uygulaması daha zordur.

SPA modeliyle mümkün kılınan Kullanıcı deneyimindeki iyileştirmeler, bu noktalara karşı karşılaştırmalı olmalıdır.

## <a name="blazor"></a>Blazor

ASP.NET Core 3,0, Blazor adlı zengin, etkileşimli ve birleştirilebilir Kullanıcı arabirimi oluşturmak için yeni bir model sunar. Blazor sunucu tarafında, geliştiricilerin sunucuda Razor ile Kullanıcı arabirimi oluşturmalarına ve bu kodun tarayıcıya teslim edilmesi ve WebAssembly adlı bir JavaScript kitaplığı aracılığıyla istemci tarafında yürütülmesi sağlanır. ASP.NET Core 3,0, hala geliştirme aşamasındadır, ancak bu e-kitap için 3,0 güncelleştirmesinde bu teknolojide daha fazla görmeyi beklemelisiniz. Blazor hakkında daha fazla bilgi için bkz. [Blazor ile çalışmaya başlama](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Geleneksel Web uygulamalarını seçme

Aşağıda, geleneksel web uygulamaları çekmeye yönelik daha önce belirtilen nedenlerden daha ayrıntılı bir açıklama verilmiştir.

**Uygulamanızda basit, muhtemelen salt okunurdur, istemci tarafı gereksinimleri vardır**

Birçok Web uygulaması öncelikle kullanıcılarının büyük bir tarafında salt okunurdur. Salt okuma (veya salt okuma) uygulamaları, büyük bir durum yaşlanmakla ve bunlarla çok daha basit olmaya eğilimlidir. Örneğin, bir arama altyapısı, arama sonuçlarını görüntülemek için bir TextBox ve ikinci bir sayfa içeren tek bir giriş noktası içerebilir. Anonim kullanıcılar kolayca istek yapabilir ve istemci tarafı mantığı için çok az gereksinim vardır. Benzer şekilde, bir blog veya içerik yönetim sisteminin herkese açık uygulaması genellikle çok sayıda istemci tarafı davranışına sahip içerikten oluşur. Bu tür uygulamalar, Web sunucusunda Logic ve tarayıcıda görüntülenecek HTML 'yi işleyen geleneksel sunucu tabanlı Web uygulamaları olarak kolayca oluşturulmuştur. Sitenin her benzersiz sayfasının, arama motorları tarafından yer işareti eklenen ve dizini oluşturulmuş bir URL 'SI vardır (varsayılan olarak, bunu uygulamanın ayrı bir özelliği olarak eklemek zorunda kalmadan), bu senaryolarda de net bir avantajdır.

**Uygulamanızın JavaScript desteği olmayan tarayıcılarda çalışması gerekiyor**

Sınırlı veya olmayan bir JavaScript desteği olan tarayıcılarda çalışması gereken Web uygulamaları, geleneksel Web uygulaması iş akışları kullanılarak yazılmalıdır (veya en azından bu davranışa geri dönebilmelidir). Maça işlevinin çalışması için istemci tarafı JavaScript gerekir; kullanılabilir değilse, maça iyi bir seçenek değildir.

**Takımınız JavaScript veya TypeScript geliştirme tekniklerini tanımıyor**

Takımınız JavaScript veya TypeScript 'i tanımıyor, ancak sunucu tarafı Web uygulaması geliştirmeyi öğreniyor, büyük olasılıkla geleneksel bir Web uygulamasını bir SPA 'dan daha hızlı bir şekilde sunabilir. Program, maça 'Ları öğrenmeye yönelik bir amaç veya bir SPA tarafından sağlanan kullanıcı deneyimi gerekli değilse, geleneksel Web Apps, bunları oluşturmaya alışkın olan takımlar için daha üretken bir seçimdir.

## <a name="when-to-choose-spas"></a>Maça ne zaman seçlik

Aşağıda, Web uygulamanız için tek sayfalı uygulamalar için geliştirme stili seçme konusunda daha ayrıntılı bir açıklama verilmiştir.

**Uygulamanız çok sayıda özelliği olan zengin bir kullanıcı arabirimi kullanıma sunmalıdır**

Maça, kullanıcılar eylem gerçekleştirirken veya uygulamanın bölgeleri arasında gezinirken sayfayı yeniden yüklemeyi gerektirmeyen zengin istemci tarafı işlevleri destekleyebilir. Maça daha hızlı yükleyebilir, arka planda veri alabilir ve tam sayfa yeniden yükleme nadir olduğundan tek tek kullanıcı eylemleri daha fazla yanıt verir. Maça, kullanıcının form göndermek için bir düğmeye tıklamasına gerek kalmadan, kısmen tamamlanmış formları veya belgeleri kaydederek Artımlı güncelleştirmeleri destekleyebilir. Maça, sürükle ve bırak gibi zengin istemci tarafı davranışlarını, geleneksel uygulamalardan çok daha kolay bir şekilde destekleyebilir. Maça bağlantısı kesik modda çalışacak şekilde tasarlanabilir ve bir bağlantı yeniden kurulduktan sonra sonunda sunucuya geri eşitlenen bir istemci tarafı modelinde güncelleştirmeler yapılır. Uygulamanızın gereksinimleri, tipik HTML formlarının sunduğu özellikleri daha fazla olan zengin işlevselliği içeriyorsa, SPA stili bir uygulama seçmeniz gerekir.

Genellikle maça 'ın, geçerli işlemi yansıtan adres çubuğunda anlamlı bir URL görüntüleme (ve bu URL 'ye dönmek için kullanıcıların yer işaretine veya derin bağlantı kurmasına izin verme) gibi geleneksel Web uygulamalarına yerleşik olan özellikleri uygulaması gerektiğini unutmayın. Ayrıca, kullanıcıların tarayıcı geri ve İleri düğmelerini Istenmeyen sonuçlarla kullanmasına izin vermeleri gerekir.

**Takımınız JavaScript ve/veya TypeScript geliştirmeyi biliyor**

Maça yazmak için JavaScript ve/veya TypeScript ile istemci tarafı programlama teknikleri ve kitaplıkları hakkında daha fazla ihtiyaç vardır. Takımınız, angular gibi bir SPA çerçevesi kullanarak modern JavaScript yazma konusunda uzmanlı olmalıdır.

> ### <a name="references--spa-frameworks"></a>Başvurular – SPA çerçeveleri
>
> - **Angular**  
>   <https://angular.io>
> - **JavaScript çerçeveleri karşılaştırması**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Uygulamanız zaten diğer (iç veya genel) istemciler için bir API 'YI kullanıma sunmalıdır**

Web API 'sini zaten başka istemciler tarafından kullanılmak üzere destekliyorsanız, sunucu tarafı formundaki mantığı yeniden oluşturmak yerine bu API 'lerden yararlanan bir SPA uygulamasının oluşturulması daha az çaba gerektirebilir. Maça, kullanıcılar uygulamayla etkileşime geçerek verileri sorgulamak ve güncelleştirmek için Web API 'lerinin kapsamlı bir şekilde kullanılmasını sağlar.

## <a name="decision-table--traditional-web-or-spa"></a>Karar tablosu – geleneksel Web veya SPA

Aşağıdaki karar tablosu, geleneksel bir Web uygulaması ve SPA arasında seçim yaparken göz önünde bulundurmanız gereken bazı temel faktörleri özetler.

| **Çarpan**                                           | **Geleneksel Web uygulaması** | **Tek Sayfalı Uygulama** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| JavaScript/TypeScript ile gerekli takım hakkında benzerlik | **En az**             | **Gerekli**                |
| Betik olmadan destek tarayıcıları                   | **Destekleniyor**           | **Desteklenmiyor**           |
| En az Istemci tarafı uygulama davranışı             | **İyi uygun**         | **Gereğinden fazla**                |
| Zengin, karmaşık kullanıcı arabirimi gereksinimleri            | **Az**             | **İyi uygun**             |

>[!div class="step-by-step"]
>[Önceki](modern-web-applications-characteristics.md)İleri
>[](architectural-principles.md)
