---
title: Kısmi hata işleme stratejileri
description: Kısmi hataların işlenmesi için çeşitli stratejileri sorunsuz bir şekilde öğrenin.
ms.date: 10/16/2018
ms.openlocfilehash: e96fe99ab44b924460e01abaad30aa3e2432117a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296049"
---
# <a name="strategies-to-handle-partial-failure"></a>Kısmi hata işleme stratejileri

Kısmi hatalarla ilgilenme stratejileri şunlardır.

**İç mikro hizmetler arasında zaman uyumsuz iletişim (örneğin, ileti tabanlı iletişim) kullanın**. İç mikro hizmetlerde zaman uyumlu HTTP çağrılarının uzun zincirlerinin oluşturulması kesinlikle önerilir, çünkü yanlış bir tasarım sonunda hatalı kesintilerin asıl nedeni olur. Aksine, istemci uygulamaları ve mikro hizmetlerin ilk düzeyi veya ayrıntılı API ağ geçitleri arasındaki ön uç iletişimleri dışında, iç mikro hizmetlerde ilk istek/yanıt döngüsünü tamamladıktan sonra yalnızca zaman uyumsuz (ileti tabanlı) iletişim kullanılması önerilir. Nihai tutarlılık ve olay odaklı mimariler, Ripple etkilerini en aza indirmenize yardımcı olur. Bu yaklaşımlar daha yüksek düzeyde mikro hizmet bağımsız çalışma sınırı uygular ve bu nedenle burada belirtilen soruna karşı engeller.

**Üstel geri alma ile yeniden denemeler kullanın**. Bu teknik, hizmetin yalnızca kısa bir süre için kullanılabilir olmaması durumunda, çağrı yeniden denemeleri belirli sayıda kez gerçekleştirerek kısa ve aralıklı hatalardan kaçınmaya yardımcı olur. Bu durum aralıklı ağ sorunları veya bir mikro hizmet/kapsayıcının bir kümedeki farklı bir düğüme taşınması nedeniyle ortaya çıkabilir. Ancak, bu yeniden denemeler devre kesiciler ile düzgün şekilde tasarlanmamışsa, bu, son olarak [hizmet reddine neden olan (DOS)](https://en.wikipedia.org/wiki/Denial-of-service_attack), Ripple efektlerini belirleyebilir.

**Ağ zaman aşımları etrafında çalışın**. Genel olarak, istemciler süresiz olarak engellenmemelidir ve yanıt beklerken her zaman zaman aşımlarını kullanır. Zaman aşımı kullanımı, kaynakların süresiz olarak hiçbir zaman bağlı olmamasını sağlar.

**Devre kesici stilini kullanın**. Bu yaklaşımda, istemci işlemi başarısız isteklerin sayısını izler. Hata oranı yapılandırılan sınırı aşarsa, daha fazla girişim başarısız olacak şekilde bir "devre kesici" gezileri olur. (Çok sayıda istek başarısız olursa, hizmetin kullanılamaz olduğunu ve gönderme isteklerinin noktasız olduğunu öneren çok sayıda istek başarısız olursa.) Bir zaman aşımı süresi dolduktan sonra, istemci yeniden denemeli ve yeni istekler başarılı olursa devre kesici ' yı kapatın.

**Fallyedekler sağlayın**. Bu yaklaşımda, istemci işlemi, önbellekteki verileri döndürme veya varsayılan bir değer gibi bir istek başarısız olduğunda geri dönüş mantığı gerçekleştirir. Bu, sorgular için uygun bir yaklaşımdır ve güncelleştirmeler veya komutlar için daha karmaşıktır.

**Sıraya alınan isteklerin sayısını sınırlayın**. İstemciler ayrıca bir istemci mikro hizmetinin belirli bir hizmete gönderemediği bekleyen istek sayısına bir üst sınır getirmelidir. Sınıra ulaşılırsa, ek istekler yapmak büyük olasılıkla daha az olabilir ve bu denemeler hemen başarısız olur. Uygulama açısından, bu gereksinimi karşılamak için Polly [Bulkbaş yalıtım](https://github.com/App-vNext/Polly/wiki/Bulkhead) ilkesi kullanılabilir. Bu yaklaşım temelde uygulama olarak <xref:System.Threading.SemaphoreSlim> bir paralelleştirme kısıtlaması olur. Ayrıca, Bulkhead dışında bir "kuyruğa" de izin verir. Yürütmeden önce bile daha fazla yük (örneğin, kapasite tam olarak kabul edildiği için). Bu, devre kesici hatalara neden olduğundan, bazı hata senaryolarına bir devre kesicinin yanıtını daha hızlı hale getirir. Bir bulkthe bulkheadpolicy nesnesi, bölme perdesi 'in ve kuyruğun ne kadar tam olduğunu gösterir ve taşma üzerine [Olaylar sunar ve](http://www.thepollyproject.org/) bu sayede otomatik yatay ölçeklendirmeyi açmak için de kullanılabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Dayanıklılık desenleri**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Esnekliği ekleme ve performans\ En Iyi duruma getirme**
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Bölme perdesi.** GitHub deposu. Polly ilkesiyle uygulama. \
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Azure\ için dayanıklı uygulamalar tasarlama**
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Geçici hata işleme**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Önceki](handle-partial-failure.md)
>[İleri](implement-retries-exponential-backoff.md)
