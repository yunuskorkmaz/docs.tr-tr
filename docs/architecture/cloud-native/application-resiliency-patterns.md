---
title: Uygulama dayanıklılığı desenleri
description: Azure için Cloud Native .NET uygulamaları tasarlama | Uygulama dayanıklılığı desenleri
ms.date: 06/30/2019
ms.openlocfilehash: 8455584fe1d5b02f6d9543c3bad32cca7369c158
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183723"
---
# <a name="application-resiliency-patterns"></a>Uygulama dayanıklılığı desenleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

İlk savunma hattı, yazılım etkin uygulama dayanıklılığı ' dır. 

Kendi dayanıklılık çatısını yazarken önemli ölçüde yatırım yapabilirsiniz, ancak bu tür ürünler zaten var. Örneğin, [Polly](http://www.thepollyproject.org/) , geliştiricilerin dayanıklılık ilkelerini akıcı ve iş parçacığı açısından güvenli bir şekilde ifade etmesine olanak tanıyan kapsamlı bir .net esnekliği ve geçici hata işleme kitaplığıdır. Tam .NET Framework veya .NET Core ile oluşturulmuş uygulamaları Polly hedefler. Şekil 6-2, Polly kitaplığından kullanılabilen dayanıklılık ilkelerini (diğer bir deyişle, işlevselliği) gösterir. Bu ilkeler ayrı ayrı uygulanabilir veya birlikte birleştirilebilir.

![Polly çerçevesi](./media/polly-resiliency-framework.png)

**Şekil 6-2**. Polly dayanıklılık çerçevesi özellikleri

Önceki şekilde, bir dış istemciden veya başka bir arka uç hizmetten gelen istek iletilerine yönelik dayanıklılık ilkelerinin nasıl uygulanacağını göz önünde bulun. Amaç, geçici olarak kullanılamayan bir hizmet için isteği telafi olmaktır. Bu kısa kesintiler genellikle Şekil 6-3 ' de gösterilen HTTP durum kodlarıyla birlikte bildirime sahiptir.

![Yeniden denenecek HTTP durum kodları](./media/http-status-codes.png)

**Şekil 6-3**. Yeniden denenecek HTTP durum kodları

Unuza 403-Yasak HTTP durum kodunu yeniden denesin mi? Hayır. Burada, sistem düzgün şekilde çalışır, ancak çağrıyı yapana istenen işlemi gerçekleştirme yetkisine sahip olmadıkları konusunda bilgilendirilir. Yalnızca hatalardan kaynaklanan işlemleri yeniden denemek için dikkatli olunmalıdır.

Bölüm 1 ' de önerildiği gibi, bulutta yerel uygulamalar oluştururken Microsoft geliştiricilerinin .NET Core 'u hedeflemesi gerekir. Sürüm 2,1, URL tabanlı kaynaklarla etkileşim kurmak için HTTP Istemci örnekleri oluşturmak üzere [Httpclientfactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) kitaplığı 'nı kullanıma sunmuştur. Özgün HTTPClient sınıfını yerine, Factory sınıfı birçok gelişmiş özelliği destekler, bunlardan biri de Polly dayanıklılık kitaplığıyla [sıkı bir şekilde tümleştirilmiştir](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) . Bununla birlikte, kısmi hataları ve bağlantı sorunlarını ele almak için uygulama başlangıç sınıfındaki dayanıklılık ilkelerini kolayca tanımlayabilirsiniz.

Sonra, yeniden deneme ve devre kesici desenlerinde genişletelim.

### <a name="retry-pattern"></a>Yeniden deneme biçimi

Dağıtılmış bir bulutta yerel ortamda, hizmet ve bulut kaynaklarına yapılan çağrılar, genellikle kısa bir süre sonra kendilerini düzelttiğinden geçici (kısa süreli) hatalardan dolayı başarısız olabilir. Yeniden deneme stratejisi uygulamak, bulutta yerel bir hizmetin bu senaryoları işlemesine yardımcı olur.

[Yeniden deneme](https://docs.microsoft.com/azure/architecture/patterns/retry) sürümü, bir hizmetin başarısız istek işlemini yeniden denemesini sağlar (yapılandırılabilir) ve bir bekleme süresini üstel olarak artırır. Şekil 6-4, bir yeniden deneme işlemini gösterir.

![Yeniden deneme deseninin eylemi](./media/retry-pattern.png)

**Şekil 6-4**. Yeniden deneme deseninin eylemi

Önceki şekilde, bir istek işlemi için yeniden deneme biçimi uygulandı. Bir geri alma aralığı (bekleme süresi) ile başarısız olmadan önce, sonraki her denemede katlanarak çift yönlü olan iki saniyeden oluşan en fazla dört denemeye izin verecek şekilde yapılandırılmıştır.

- İlk çağırma başarısız olur ve 500 HTTP durum kodunu döndürür. Uygulama iki saniye bekler ve çağrıyı yeniden oluşturur.
- İkinci çağrı da başarısız olur ve 500 HTTP durum kodunu döndürür. Uygulama artık geri alma aralığını dört saniyeye ikiye katlanır ve çağrıyı yeniden dener.
- Son olarak, üçüncü çağrı başarılı olur.
- Bu senaryoda, yeniden deneme işlemi, çağrı başarısız olmadan önce geri alma süresini ikiye katlarken dört yeniden denemeye girişdi.

Hizmet süresinin kendine doğru olması için çağrıyı yeniden denemeden önce geri alma döneminin artırılması önemlidir. Yeterli düzeltme süresine izin vermek için, sınırsız bir şekilde artan bir artırma (her yeniden denemeli dönemi katlama) uygulamak en iyi uygulamadır.

## <a name="circuit-breaker-pattern"></a>Devre kesici stili

Yeniden deneme stili, bir isteği kısmi bir hata halinde ölçeklendirmesine yardımcı olmakla kalmaz, hataların daha uzun süre içinde çözülmesi gereken beklenmeyen olaylar nedeniyle hatalara neden olabilecek durumlar vardır. Bu hatalar, bir hizmetin tamamen başarısızlığına yönelik kısmi bir bağlantı kaybından önem düzeyi olarak değişebilir. Bu durumlarda, bir uygulamanın başarılı olması olası olmayan bir işlemi sürekli olarak yeniden denemesi için daha az kullanılır.

Nesnelerin daha kötü olması için, yanıt vermeyen bir hizmette sürekli yeniden deneme işlemleri yürütmek, sizi, bellek, iş parçacıkları ve veritabanı gibi kaynakları tükettiğini önemli bir çağrı ile yaptığınız otomatik olarak belirlenen bir hizmet reddi senaryosuna taşıyabilirler. bağlantılar, sistemin aynı kaynakları kullanan ilişkisiz kısımlarında hata vermesine neden olur.

Bu durumlarda, işlemin hemen başarısız olması ve yalnızca başarılı olma olasılığı varsa hizmeti çağırmayı denemesi tercih edilir.

[Devre kesici stili](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) , bir uygulamanın başarısız olma olasılığı olan bir işlemi tekrar tekrar yürütmeye engel olabilir. Ayrıca, hatanın çözümlenip çözümlenmediğini belirlemede düzenli bir deneme çağrısıyla uygulamayı izler. Şekil 6-5, devre kesici düzeninin eylemde olduğunu gösterir.

![Devreye ayırıcı stili eylem içinde](./media/circuit-breaker-pattern.png)

**Şekil 6-5**. Devreye ayırıcı stili eylem içinde

Önceki şekilde, özgün yeniden deneme düzenine bir devre kesici stili eklenmiştir. 10 başarısız istekten sonra devre ayırıcılarını açıp artık hizmete çağrı yapılmasına izin vermez. Checkdevresi değeri 30 saniye olarak ayarlandığında, kitaplığın bir isteğin hizmete ne sıklıkta devam etmesine izin verdiğini belirtir. Bu çağrı başarılı olursa, devre kapanır ve hizmet tekrar trafik için kullanılabilir olur.

Devre kesici deseninin amacını, yeniden deneme düzeninden *farklı* olduğunu aklınızda bulundurun. Yeniden deneme stili, bir uygulamanın başarılı olacağı beklentide bir işlemi yeniden denemesini sağlar. Devre kesici stili, bir uygulamanın başarısız olma olasılığı olan bir işlem gerçekleştirmesini engeller. Genellikle, bir uygulama devre kesici aracılığıyla bir işlemi çağırmak için yeniden deneme desenini kullanarak bu iki deseni *birleştirir* . Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen özel durumlara duyarlı olmalıdır ve devre kesici bir hatanın geçici olmadığını gösteriyorsa yeniden deneme girişimlerini iptal edin.

Uygulama dayanıklılığı, sorunlu istenen işlemleri işlemek için gereklidir. Ancak, hikayenin yalnızca yarısı vardır. Daha sonra, Azure bulutu 'nda bulunan dayanıklılık özelliklerini ele aldık.

>[!div class="step-by-step"]
>[Önceki](resiliency.md)
>[İleri](infrastructure-resiliency-azure.md)
