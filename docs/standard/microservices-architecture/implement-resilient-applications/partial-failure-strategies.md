---
title: Kısmi hata işleme stratejileri
description: Kısmi hataları düzgün bir şekilde işlemek için çeşitli stratejileri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: ad45e357c1656b9346b7bdb5f324bde5fa76eaba
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362775"
---
# <a name="strategies-to-handle-partial-failure"></a>Kısmi hata işleme stratejileri

Kısmi hatalarıyla ilgili stratejiler aşağıda verilmiştir.

**İç mikro hizmetler arasında zaman uyumsuz iletişim (örneğin, ileti tabanlı iletişim) kullanan**. Bu yanlış tasarım sonunda hatalı kesintiler ana nedenini olur çünkü zaman uyumlu HTTP çağrıları için uzun zincirleri iç mikro hizmetler arasında oluşturmamayı yüksek oranda önerilir. Tam, istemci uygulamalar ve mikro hizmetler veya ayrıntılı API ağ geçitleri ilk düzeyi arasında ön uç iletişim dışında (yalnızca zaman uyumsuz ileti tabanlı) iletişim ilk istek son kez kullanılması önerilir / İç mikro hizmetler arasında yanıt döngüsü. Son tutarlılık ve olaya dayalı mimariler ripple etkileri en aza indirmek için yardımcı olur. Bu yaklaşımların mikro hizmet bağımsız çalışma sınırı daha yüksek bir düzeyde uygulamak ve bu nedenle burada bahsedilen sorun karşı önleme.

**Üstel geri alma ile yeniden denemeleri kullanma**. Bu teknik kısa kaçınmaya yardımcı olur ve çağrı yaparak aralıklı hatalar yalnızca kısa bir süre için hizmet kullanılamıyor durumunda belirli sayıda bir kez yeniden dener. Bu, aralıklı ağ sorunlarından kaynaklanan veya bir mikro hizmet/kapsayıcı farklı bir düğüme bir küme içinde taşındığında ortaya çıkabilir. Bu yeniden deneme devre Kesiciler ile düzgün şekilde tasarlanmamıştır, ancak bunu ripple etkileri aggravate sonuçta bile neden olan bir [hizmet reddi (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Ağ zaman aşımı geçici**. Genel olarak, istemciler süresiz olarak Engellemesi değil ve her zaman bir yanıtı beklenirken zaman aşımı kullanacak şekilde tasarlanmalıdır. Zaman aşımı kullanarak kaynakları hiçbir zaman süresiz olarak bağlı olduğunu sağlar.

**Devre kesici düzeni kullanmak**. Bu yaklaşımda, istemci işlemi başarısız istek sayısını izler. Daha fazla denemeleri hemen başarısız olduğunu hata oranı "devre kesici" gelişlerin yapılandırılmış bir sınır aşarsa. (Çok sayıda istek başarısız oluyorsa, hizmet kullanılamıyor ve istekleri gönderirken anlamsız olduğunu önerir.) Bir zaman aşımı süresinden sonra istemci yeniden deneyin ve gerekir, yeni istekler başarılı olursa, devre kesici kapatılır.

**Geri dönüşleri sağlamak**. Önbelleğe alınmış verileri veya varsayılan değeri döndürme gibi bir istek başarısız olduğunda bu yaklaşımda, geri dönüş mantığı istemci işlemini gerçekleştirir. Bu sorgular için uygun bir yaklaşım ve güncelleştirmeleri veya komutları için daha karmaşıktır.

**Kuyruğa alınan istekler sayısını sınırlayın**. İstemciler ayrıca bir istemci bir mikro hizmet belirli bir hizmete gönderebilirsiniz bekleyen istek sayısı üst sınırı dayatır. Sınırına ulaşıldı, ek isteğinde bulunmak büyük olasılıkla anlamsız ve bu girişimler hemen başarısız olması. Uygulama, Polly açısından [bölme perdesi yalıtım](https://github.com/App-vNext/Polly/wiki/Bulkhead) İlkesi, bu gereksinimi karşılamak için kullanılabilir. Aslında bir paralelleştirme azaltma ile bu yaklaşım, <xref:System.Threading.SemaphoreSlim> uygulaması olarak. Bölme perdesi dışında bir "sıra" izin verir. (Örneğin, kapasite tam kabul edilir çünkü) aşırı yük yürütme önce proaktif olarak boşaltmaktır. Bu belirli hata senaryoları yanıtını hataları için devre kesici bekler olduğundan devre kesici, daha hızlı sağlar. BulkheadPolicy nesnesinde [Polly](http://www.thepollyproject.org/) kullanıma sunan nasıl tam bölme perdesi ve sırası olduğu ve teklifler olayları taşmada bu nedenle de kullanılabilir sürücü otomatik yatay ölçekleme için.

## <a name="additional-resources"></a>Ek kaynaklar

- **Dayanıklılık desenleri**\
  [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](/azure/architecture/patterns/category/resiliency)

- **Dayanıklılık ekleme ve performansı en iyi duruma getirme**\
  [*https://msdn.microsoft.com/library/jj591574.aspx*](https://msdn.microsoft.com/library/jj591574.aspx)

- **Bölme perdesi.** GitHub deposu. Polly ilke uygulamasıyla. \
  [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

- **Azure için dayanıklı uygulamalar tasarlama**\
  [*https://docs.microsoft.com/azure/architecture/resiliency/*](/azure/architecture/resiliency/)

- **Geçici hata işleme**\
  [*https://docs.microsoft.com/azure/architecture/best-practices/transient-faults*](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Önceki](handle-partial-failure.md)
>[İleri](implement-retries-exponential-backoff.md)