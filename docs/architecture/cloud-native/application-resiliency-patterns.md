---
title: Uygulama dayanıklılığı desenleri
description: Azure için Cloud Native .NET uygulamaları tasarlama | Uygulama dayanıklılığı desenleri
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: e81d6e1d6b95cf0053de3ba557068ff458a59dc9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161158"
---
# <a name="application-resiliency-patterns"></a>Uygulama dayanıklılığı desenleri

İlk savunma hattı uygulama dayanıklılığı ' dır.

Kendi dayanıklılık çatısını yazarken önemli ölçüde yatırım yapabilirsiniz, ancak bu tür ürünler zaten var. [Polly](http://www.thepollyproject.org/) , geliştiricilerin dayanıklılık ilkelerini akıcı ve iş parçacığı açısından güvenli bir şekilde ifade etmesine olanak tanıyan kapsamlı bir .net esnekliği ve geçici hata işleme kitaplığıdır. .NET Framework veya .NET Core ile oluşturulan uygulamaları Polly hedefler. Aşağıdaki tabloda `policies` , Polly kitaplığı 'nda bulunan olarak adlandırılan dayanıklılık özellikleri açıklanmaktadır. Bunlar ayrı ayrı uygulanabilir veya birlikte gruplandırılabilir.

| İlke | Deneyim |
| :-------- | :-------- |
| Yeniden Dene | Belirlenen işlemlerde yeniden deneme işlemlerini yapılandırır. |
| Devre Kesici | Hatalar yapılandırılan eşiği aştığında önceden tanımlanmış bir süre için istenen işlemleri engeller |
| Zaman aşımı | Bir arayanın yanıt bekleneceği süreye göre sınır koyar. |
| Bölme Perdesi | Bir kaynağın çok fazla başarısız olan aramalarını engellemek için eylemleri sabit boyutlu kaynak havuzuna kısıtlar. |
| Önbellek | Yanıtları otomatik olarak depolar. |
| Geri dönüş | Hata durumunda yapılandırılmış davranışı tanımlar. |

Önceki şekilde, bir dış istemciden veya arka uç hizmetinden gelen istek iletilerine yönelik dayanıklılık ilkelerinin nasıl uygulanacağını göz önünde bulun. Amaç, geçici olarak kullanılamayan bir hizmet için isteği telafi olmaktır. Bu kısa süreli kesintiler tipik olarak, aşağıdaki tabloda gösterilen HTTP durum kodlarıyla birlikte yapılır.

| HTTP durum kodu| Nedeni |
| :-------- | :-------- |
| 404 | Bulunamadı |
| 408 | İstek zaman aşımı |
| 429 | Çok fazla istek (büyük olasılıkla kısıtlamış olabilirsiniz) |
| 502 | Hatalı ağ geçidi |
| 503 | Hizmet kullanılamıyor |
| 504 | Ağ geçidi zaman aşımı |

Soru: 403-Yasak HTTP durum kodunu yeniden denesin mi? Hayır. Burada, sistem düzgün şekilde çalışır, ancak çağrıyı yapana istenen işlemi gerçekleştirme yetkisine sahip olmadıkları konusunda bilgilendirilir. Yalnızca hatalardan kaynaklanan işlemleri yeniden denemek için dikkatli olunmalıdır.

Bölüm 1 ' de önerildiği gibi, bulutta yerel uygulamalar oluştururken Microsoft geliştiricilerinin .NET Core platformunu hedeflemesi gerekir. Sürüm 2,1, URL tabanlı kaynaklarla etkileşim kurmak için HTTP Istemci örnekleri oluşturmak üzere [Httpclientfactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) kitaplığı 'nı kullanıma sunmuştur. Özgün HTTPClient sınıfını yerine, Factory sınıfı birçok gelişmiş özelliği destekler, bunlardan biri de Polly dayanıklılık kitaplığıyla [sıkı bir şekilde tümleştirilmiştir](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) . Bununla birlikte, kısmi hataları ve bağlantı sorunlarını ele almak için uygulama başlangıç sınıfındaki dayanıklılık ilkelerini kolayca tanımlayabilirsiniz.

Sonra, yeniden deneme ve devre kesici desenlerinde genişletelim.

### <a name="retry-pattern"></a>Yeniden deneme düzeni

Dağıtılmış bir bulutta yerel ortamda, hizmet ve bulut kaynaklarına yapılan çağrılar, genellikle kısa bir süre sonra kendilerini düzelttiğinden geçici (kısa süreli) hatalardan dolayı başarısız olabilir. Yeniden deneme stratejisi uygulamak, bulutta yerel bir hizmetin bu senaryoları azaltmasının sağlanmasına yardımcı olur.

[Yeniden deneme](/azure/architecture/patterns/retry) sürümü, bir hizmetin başarısız istek işlemini yeniden denemesini sağlar (yapılandırılabilir) ve bir bekleme süresini üstel olarak artırır. Şekil 6-2, bir yeniden deneme işlemini gösterir.

![Yeniden deneme deseninin eylemi](./media/retry-pattern.png)

**Şekil 6-2**. Yeniden deneme deseninin eylemi

Önceki şekilde, bir istek işlemi için yeniden deneme biçimi uygulandı. Bir geri alma aralığı (bekleme süresi) ile başarısız olmadan önce, sonraki her denemede katlanarak çift yönlü olan iki saniyeden oluşan en fazla dört denemeye izin verecek şekilde yapılandırılmıştır.

- İlk çağırma başarısız olur ve 500 HTTP durum kodunu döndürür. Uygulama iki saniye bekler ve çağrıyı yeniden dener.
- İkinci çağrı da başarısız olur ve 500 HTTP durum kodunu döndürür. Uygulama artık geri alma aralığını dört saniyeye ikiye katlanır ve çağrıyı yeniden dener.
- Son olarak, üçüncü çağrı başarılı olur.
- Bu senaryoda, yeniden deneme işlemi, çağrı başarısız olmadan önce geri alma süresini ikiye katlarken dört yeniden denemeye girişdi.
- 4 yeniden deneme denemesi başarısız oldu, sorunu düzgün şekilde işlemek için bir geri dönüş ilkesi çağırılır.

Hizmet süresinin kendine doğru olması için çağrıyı yeniden denemeden önce geri alma döneminin artırılması önemlidir. Yeterli düzeltme süresine izin vermek için, sınırsız bir şekilde artan bir artırma (her yeniden denemeli dönemi katlama) uygulamak en iyi uygulamadır.

## <a name="circuit-breaker-pattern"></a>Devre kesici stili

Yeniden deneme stili, bir isteği kısmi bir hata halinde ölçeklendirmesine yardımcı olmakla kalmaz, hataların daha uzun süre içinde çözülmesi gereken beklenmeyen olaylar nedeniyle hatalara neden olabilecek durumlar vardır. Bu hataların önem derecesi kısmi bağlantı kaybıyla bir hizmetin tamamen çökmesi arasında değişebilir. Bu durumlarda, bir uygulamanın başarılı olması olası olmayan bir işlemi sürekli olarak yeniden denemesi için daha az kullanılır.

Kötü, yanıt vermeyen bir hizmette sürekli yeniden deneme işlemleri gerçekleştirmek için, önemli olmayan bir hizmette sürekli olarak gerçekleştirilen bir hizmet reddi senaryosuna taşınabilir ve bu da, bellek, iş parçacıkları ve veritabanı bağlantıları gibi kaynakları tüketerek, aynı kaynakları kullanan sistemin ilgisiz kısımlarında hata oluşmasına neden olabilir.

Bu durumlarda, işlemin hemen başarısız olması ve yalnızca başarılı olma olasılığı varsa hizmeti çağırmayı denemesi tercih edilir.

[Devre kesici stili](/azure/architecture/patterns/circuit-breaker) , bir uygulamanın başarısız olma olasılığı olan bir işlemi tekrar tekrar yürütmeye engel olabilir. Önceden tanımlı bir dizi başarısız çağrı yapıldıktan sonra, hizmete giden tüm trafiği engeller. Düzenli aralıklarla, hatanın çözümlenip çözümlenmediğini tespit etmek için bir deneme çağrısına izin verir. Şekil 6-3, devre kesici düzeninin eylemde olduğunu gösterir.

![Devreye ayırıcı stili eylem içinde](./media/circuit-breaker-pattern.png)

**Şekil 6-3**. Devreye ayırıcı stili eylem içinde

Önceki şekilde, özgün yeniden deneme düzenine bir devre kesici stili eklenmiştir. 100 başarısız isteklerin nasıl yapılacağı, devre kesicilerin açılmadığını ve hizmete çağrı yapılmasına izin vermez. Checkdevresi değeri 30 saniye olarak ayarlandığında, kitaplığın bir isteğin hizmete ne sıklıkta devam etmesine izin verdiğini belirtir. Bu çağrı başarılı olursa, devre kapanır ve hizmet tekrar trafik için kullanılabilir olur.

Devre kesici deseninin amacını, yeniden deneme düzeninden *farklı* olduğunu aklınızda bulundurun. Yeniden deneme stili, bir uygulamanın başarılı olacağı beklentide bir işlemi yeniden denemesini sağlar. Devre kesici stili, bir uygulamanın başarısız olma olasılığı olan bir işlem gerçekleştirmesini engeller. Genellikle, bir uygulama devre kesici aracılığıyla bir işlemi çağırmak için yeniden deneme desenini kullanarak bu iki deseni *birleştirir* .

## <a name="testing-for-resiliency"></a>Dayanıklılığı test etme

Dayanıklılık testi, uygulama işlevlerini test ettiğiniz şekilde (birim testlerini, tümleştirme testlerini vb.) her zaman yapılamaz. Bunun yerine, yalnızca zaman zaman ortaya çıkan hata koşulları altında uçtan uca iş yükünün ne performans göstereceğini test etmeniz gerekir. Örneğin: işlemlere kilitlenme, süre dolma sertifikaları, bağımlı hizmetleri kullanılamaz hale getirerek ekleme. [Chaos-maymun](https://github.com/Netflix/chaosmonkey) gibi çerçeveler, böyle bir Chaos testi için kullanılabilir.

Uygulama dayanıklılığı, sorunlu istenen işlemleri işlemek için gereklidir. Ancak, hikayenin yalnızca yarısı vardır. Daha sonra, Azure bulutu 'nda bulunan dayanıklılık özelliklerini ele aldık.

>[!div class="step-by-step"]
>[Önceki](resiliency.md) 
> [Sonraki](infrastructure-resiliency-azure.md)
