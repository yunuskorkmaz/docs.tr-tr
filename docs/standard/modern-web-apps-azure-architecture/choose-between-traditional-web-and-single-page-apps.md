---
title: Geleneksel web uygulamaları ile tek sayfa uygulamaları arasında seçim yapma
description: Web uygulamaları oluştururken geleneksel web uygulamaları ve tek sayfa uygulamaları (Spa'lar) arasında seçim yapma öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 6/28/2018
ms.openlocfilehash: 40b17d07b008c2a3a9457bffc26b612e6b5c9fe5
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404157"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Geleneksel Web uygulamaları ile tek sayfa uygulamaları (Spa'lar) arasında seçim yapma

> "Atwood'ın yasaları: JavaScript'te yazılmış herhangi bir uygulama JavaScript'te sonunda yazılır."  
> _\- Jeff Atwood_

Bugün web uygulamaları oluşturmak için iki genel yaklaşım vardır: sunucu ve tek sayfa uygulamaları (Spa'lar) bir web tarayıcısında kullanıcı arabirimi mantığının çoğunu gerçekleştirmek uygulama mantığı çoğunu gerçekleştir geleneksel web uygulamaları öncelikle web API'leri kullanarak web sunucusu ile iletişim kurma. Karma bir yaklaşım da mümkündür, en basit olan konak bir veya daha fazla zengin SPA benzeri alt uygulamalar daha büyük geleneksel web uygulaması içinde.

Geleneksel web uygulamaları kullanmanız gerektiği zaman:

- Basit veya salt okunur bile, uygulamanızın istemci-tarafı gereksinimleri verilmiştir.

- Tarayıcılarında JavaScript desteğiyle çalışabilmesi uygulamanız gerekir.

- Takımınızın geliştirme tekniklerini JavaScript veya TypeScript ile tanınmıyor.

Bir SPA kullanmanız gerektiği zaman:

- Uygulamanızı, birçok özellik ile zengin kullanıcı arabirimi kullanıma sunması gerekir.

- Takımınız, JavaScript ve/veya TypeScript geliştirmeyle.

- Uygulamanız zaten diğer (dahili veya genel) istemciler için bir API göstermesi gerekir.

SPA çerçeveleri büyük gerektiren ek olarak, mimari ve güvenlik uzmanlığı. Bunlar, büyük veri değişim sıklığı nedeniyle sık sık güncelleştirme ve yeni çerçeveleri daha geleneksel web uygulamaları karşılaşırsınız. Otomatik derleme ve dağıtım işlemleri yapılandırma ve kapsayıcıları gibi dağıtım seçenekleri yararlanarak geleneksel web uygulamaları SPA uygulamalarla daha zordur.

Kullanıcı deneyiminde SPA modeli tarafından olası yapılan geliştirmeler, bu konuları karşı ağırlıklı gerekir.

## <a name="when-to-choose-traditional-web-apps"></a>Ne zaman geleneksel web uygulamaları seçin

Çekme geleneksel web uygulamaları için daha önce belirtilen nedenlerden daha ayrıntılı bir açıklaması verilmiştir.

**Uygulamanız basit, salt okunur büyük olasılıkla, istemci-tarafı gereksinimleri vardır**

Birçok web uygulamaları, öncelikli olarak salt okunur bir biçimde kullanıcılarının büyük çoğunluğu tarafından tüketilir. Salt okunur (veya okuma çoğunlukla) uygulamaları, çok daha kolaydır, bakımını ve durum önemli miktarda işleme alınanlardan olma eğilimindedir. Örneğin, bir arama motoru, bir metin kutusu ve arama sonuçlarını görüntülemek için ikinci bir sayfa ile tek giriş noktası oluşabilir. Anonim kullanıcılar kolayca istekleri yapabilir ve istemci tarafı mantığı için pek gereksinim yoktur. Benzer şekilde, bir blog veya içerik yönetim sisteminin genel kullanıma yönelik uygulama, biraz istemci tarafı davranışı içerikle esas olarak, genellikle oluşur. Tür uygulamalar web sunucusunda mantığını gerçekleştirebilir ve tarayıcıda görüntülenecek HTML işleme geleneksel sunucu tabanlı web uygulamaları kolayca oluşturulur. Her sitenin benzersiz sayfasını bozulmasına ve (varsayılan olarak bu uygulamanın ayrı bir özellik olarak eklemek zorunda kalmadan) arama motorları tarafından dizine kendi URL sahip olmasına da Temizle senaryolarda avantajdır.

**Uygulamanızın tarayıcılarında JavaScript desteğiyle çalışması için gereken**

Kısıtlı veya JavaScript desteği olan tarayıcılarda çalışması için web uygulamaları geleneksel web uygulama iş akışları kullanılarak yazılmış olması gerekir (veya benzer bir davranış dönmesi için en az). Spa'lar çalışabilmesi için istemci tarafı JavaScript gerektirir; Spa'lar kullanılabilir durumda değilse, iyi bir seçim değildir.

**Takımınızın geliştirme tekniklerini JavaScript veya TypeScript ile tanınmıyor**

Ardından takımınız, JavaScript veya TypeScript ile yabancıysa ancak sunucu tarafı web uygulama geliştirmeyle, bunlar büyük olasılıkla geleneksel web uygulaması bir SPA daha hızlı teslim edebilirsiniz olacaktır. Öğrenme program Spa'lar için bir hedef, veya bir SPA tarafından gösterilen kullanıcı deneyimini gereklidir sürece, geleneksel web uygulamaları oluşturma ile ilgili bilgi sahibi olan takımlar için daha üretken bir seçimdir.

## <a name="when-to-choose-spas"></a>Ne zaman Spa'lar seçin

Geliştirme web uygulamanız için bir tek sayfalık uygulamalar stili seçmek ne zaman daha ayrıntılı bir açıklaması verilmiştir.

**Uygulamanızı birçok özelliği ile zengin kullanıcı arabirimi kullanımına sunun**

Spa'lar kullanıcı eylemleri veya uygulamanın bölgeler arasında gezinmek için sayfayı yeniden yüklemeyi gerektirmeyen zengin istemci tarafı işlevleri destekler. Spa'lar, daha hızlı bir şekilde veri arka planda getirme yükleyebilir ve tam sayfada yüklemelere nadir olduğundan tek tek kullanıcı eylemlerini daha hızlı yanıt. Spa'lar kısmen tamamlanmış forms veya belgeler form göndermek için bir düğmeye tıklayın girmelerine gerek kaydetme artımlı güncelleştirmeleri destekler. Spa'lar sürükle ve bırak gibi zengin istemci tarafı davranışları geleneksel uygulamaları çok daha kolay destekleyebilirsiniz. Spa'lar güncelleştirmeler yapma bağlantı yeniden kurulur kurulmaz sunucuya geri sonunda eşitlenen bir istemci-tarafı modeli için bir bağlantı kesik modda çalışacak şekilde tasarlanabilir. Uygulamanızın gereksinimlerini tipik HTML formları teklif ötesine giden zengin işlevleri eklerseniz SPA stil uygulama seçmeniz gerekir.

Sık Spa'lar için anlamlı bir URL adresi çubuk geçerli işlem yansıtma (ve kullanıcılarının yer işaretine veya bu URL için ayrıntılı bağlantı geri) görüntüleme gibi geleneksel web uygulamaları, yerleşik özellikleri uygulamak gerektiğini unutmayın. Spa'lar Ayrıca kullanıcılar tarayıcının geri ve İleri düğmelerini bunları sürpriz olmaz sonuçla kullanmak izin vermelidir.

**Takımınız, JavaScript ve/veya TypeScript geliştirmeyle**

Spa'lar yazma, JavaScript ve/veya TypeScript ve istemci tarafı programlama teknikleri ve kitaplıkları ile aşinalık gerekir. Takımınızın Angular gibi bir SPA framework kullanarak modern JavaScript yazılırken yetkin olmalıdır.

> ### <a name="references--spa-frameworks"></a>Başvuruları – SPA çerçeveleri
>
> - **Angular**  
>   <https://angular.io>
> - **JavaScript çerçevesini karşılaştırma**  
>   <https://javascriptreport.com/the-ultimate-guide-to-javascript-frameworks/>

**Uygulamanız diğer (dahili veya genel) istemciler için zaten bir API kullanıma açmalıdır**

Diğer istemciler tarafından kullanılacak bir web API'sini zaten destekliyor, mantık, sunucu tarafı formu yeniden oluşturma yerine bu API'leri yararlanan bir SPA uygulamasını oluşturmak için daha az çaba gerektirebilir. Kullanıcılar uygulama ile etkileşim kurarken Spa'lar kapsamlı kullanımını web API'leri için veri sorgulamak ve güncelleştirme olun.

## <a name="decision-table--traditional-web-or-spa"></a>Karar tablosu – geleneksel Web veya SPA

Aşağıdaki karar tablosu için temel faktör, geleneksel web uygulaması ve bir SPA arasında seçim yapılırken dikkate alınacak bazı özetlenmektedir.

| **faktörü**                                           | **Geleneksel Web uygulaması** | **Tek Sayfalı Uygulama** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| JavaScript/TypeScript konusunda gerekli ekip | **En az**             | **Gerekli**                |
| R betiği oluşturmanıza destek tarayıcılar                   | **Desteklenen**           | **Desteklenmiyor**           |
| En düşük istemci tarafında uygulama davranışı             | **Uygundur**         | **Düşünülecek**                |
| Zengin, karmaşık kullanıcı arabirimi gereksinimleri            | **Sınırlı**             | **Uygundur**             |

>[!div class="step-by-step"]
[Önceki](modern-web-applications-characteristics.md)
[İleri](architectural-principles.md)
