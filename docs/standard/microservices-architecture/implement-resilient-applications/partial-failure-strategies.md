---
title: Kısmi hata işleme stratejileri
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Kısmi hata işleme stratejileri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c36ea31ad19b02fb02bc8e7185bfe8687b87764f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104215"
---
# <a name="strategies-for-handling-partial-failure"></a>Kısmi hata işleme stratejileri

Kısmi hatalar postalarla stratejileri arasında şunlar yer alır.

**Zaman uyumsuz iletişim (örneğin, ileti tabanlı iletişim) iç mikro kullanmak**. Bu yanlış tasarımı sonunda hatalı kesintileri ana neden olacak çünkü uzun zincirleri zaman uyumlu HTTP çağrıları arasında iç mikro oluşturun değil yüksek oranda önerilir. Tersine, istemci uygulamaları mikro veya hassas API ağ geçitleri ilk düzeyi arasında ön uç iletişim dışında yalnızca zaman uyumsuz (ileti tabanlı) iletişim ilk istek geçmiş kez kullanmak için önerilir / İç mikro arasında yanıt döngüsü. Nihai tutarlılık ve olay denetimli mimarileri ripple etkileri en aza indirmek için yardımcı olur. Bu yaklaşım mikro hizmet otonomisi daha yüksek düzeyde zorlamak ve bu nedenle burada bahsedilen sorun karşı engelleyebilirsiniz.

**Yeniden deneme üstel geri alma ile kullanmak**. Bu teknik kısa önlenmesine yardımcı olur ve çağrı yaparak aralıklı hatalar yeniden deneme zaman, belirli bir sayıda hizmet yalnızca kısa bir süre için kullanılamadığı durumda. Bu, zaman zaman ortaya çıkan ağ sorunları nedeniyle veya mikro hizmet/kapsayıcı farklı bir düğüme bir küme içinde taşındığında ortaya çıkabilir. Bu deneme hattı ayırıcıları ile düzgün şekilde tasarlanmamıştır, ancak bunu ripple etkilerini aggravate sonuçta bile neden olan bir [hizmet reddi (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Ağ zaman aşımı geçici**. Genel olarak, istemciler süresiz olarak engellemeyi değil ve her zaman için bir yanıt beklenirken zaman aşımı kullanmak üzere tasarlanmalıdır. Zaman aşımları kullanarak kaynakları hiçbir zaman süresiz olarak bağlıdır olduğunu sağlar.

**Devre kesici desenini kullanan**. Bu yaklaşımda, istemci işleminin başarısız isteklerin sayısını izler. Böylece hemen başka denemeleri başarısız hata oranı "devre kesici" dönüşleri yapılandırılmış bir sınır aşarsa. (Çok sayıda isteği başarısız oluyorsa, hizmet kullanılamıyor ve istekleri gönderirken bir durum olduğunu önerir.) Zaman aşımı süresinden sonra istemci yeniden deneyin ve, yeni istekleri başarılı olup olmadığını devre kesici kapatın.

**Geri dönüşler sağlamak**. Önbelleğe alınan veriler veya varsayılan değeri döndüren gibi bir isteği başarısız olduğunda bu yaklaşım, geri dönüş mantığı istemci işlemini gerçekleştirir. Bu sorguları için uygun bir yaklaşım ve güncelleştirmeleri veya komutları için daha karmaşıktır.

**Sıraya alınan istek sayısı sınırı**. İstemciler ayrıca bir istemci mikro hizmet belirli bir hizmet gönderebilirsiniz bekleyen istek sayısı üst sınırı zorunlu tuttukları. Sınıra ulaştıysanız ek istekler yapmasını büyük olasılıkla bir durum ve bu girişimler hemen başarısız olması. Uygulama, Polly açısından [Bulkhead yalıtım](https://github.com/App-vNext/Polly/wiki/Bulkhead) İlkesi, bu gereksinimi karşılamak için kullanılabilir. Bu yaklaşım temelde paralelleştirme azaltma ile olan <xref:System.Threading.SemaphoreSlim> uygulaması olarak. Ayrıca, bulkhead dışında bir "sıra" verir. (Örneğin, kapasite tam kabul edilir çünkü) yürütmeden önce bile aşırı yük proaktif olarak shed. Bu yanıt belirli hata senaryoları için devre kesici hataları için bekleyeceği beri devre kesici olması durumuna göre hızlandırır. Polly BulkheadPolicy nesnesinde nasıl tam bulkhead gösterir ve sıra olan ve taşma teklifleri olaylarına bu nedenle de Otomatik yatay ölçekleme sürücü için kullanılabilir.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Dayanıklılık desenleri**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Esnekliği ekleme ve performansı en iyi duruma getirme**
    [*https://msdn.microsoft.com/library/jj591574.aspx*](https://msdn.microsoft.com/library/jj591574.aspx)

-   **Bulkhead.** GitHub depo. Uygulama Polly ilkesiyle. \
    [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Azure için esnek uygulamalar tasarlama**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **Geçici hata işleme**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[Önceki](handle-partial-failure.md)
[sonraki](implement-retries-exponential-backoff.md)
