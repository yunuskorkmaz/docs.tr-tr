---
title: Kısmi hata işleme stratejileri
description: Kısmi hataları incelikle işlemek için çeşitli stratejiler tanıyın.
ms.date: 10/16/2018
ms.openlocfilehash: e96fe99ab44b924460e01abaad30aa3e2432117a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296049"
---
# <a name="strategies-to-handle-partial-failure"></a>Kısmi başarısızlığı işlemek için stratejiler

Kısmi hatalarla başa çıkmak için stratejiler şunlardır.

**Dahili mikro hizmetler arasında eşzamanlı iletişim (örneğin, ileti tabanlı iletişim) kullanın.** Bu yanlış tasarım sonunda kötü kesintilerin ana nedeni haline gelecektir, çünkü iç mikrohizmetler arasında senkron HTTP aramaları uzun zincirleri oluşturmak için son derece tavsiye edilir. Tam tersine, istemci uygulamaları ile ilk mikro hizmetler düzeyi veya ince taneli API Ağ geçitleri arasındaki ön uç iletişimi dışında, ilk istek/yanıt döngüsünü geçtikten sonra, dahili mikro hizmetler arasında yalnızca eşzamanlı (ileti tabanlı) iletişim kullanılması önerilir. Nihai tutarlılık ve olay odaklı mimariler dalgalanma etkilerini en aza indirmek için yardımcı olacaktır. Bu yaklaşımlar daha yüksek düzeyde mikro hizmet özerkliği uygular ve bu nedenle burada belirtilen soruna karşı önlemek.

**Üstel geri dönüşlü yeniden denemeleri kullanın.** Bu teknik, hizmetin yalnızca kısa bir süre için kullanılamaması durumunda, çağrı yeniden denemelerini belirli sayıda gerçekleştirerek kısa ve aralıklı hataları önlemeye yardımcı olur. Bu, aralıklı ağ sorunları nedeniyle veya bir microservice/kapsayıcı kümede farklı bir düğüme taşındığında oluşabilir. Ancak, bu yeniden denemeler devre kesicilerle düzgün bir şekilde tasarlanmazsa, dalgalanma etkilerini ağırlaştırabilir ve sonuçta [Hizmet Reddi 'ne (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)bile neden olabilir.

**Ağ zaman zaman larını geçici olarak çalıştırın.** Genel olarak, istemciler süresiz olarak engellemek ve bir yanıt beklerken her zaman zaman zaman ekinleri kullanmak için tasarlanmış olmalıdır. Zaman zaman zaman larını kullanmak, kaynakların asla sonsuza kadar bağlanmamasını sağlar.

**Devre Kesici deseni kullanın.** Bu yaklaşımda, istemci işlemi başarısız isteklerin sayısını izler. Hata oranı yapılandırılmış bir sınırı aşarsa, bir "devre kesici" sürükler, böylece daha fazla girişim hemen başarısız olur. (Çok sayıda istek başarısız oluyorsa, bu hizmetin kullanılmadığını ve istek göndermenin anlamsız olduğunu gösterir.) Bir zaman adabı döneminden sonra istemci yeniden denemeli ve yeni istekler başarılı olursa devre kesiciyi kapatmalıdır.

**Geri dönüşler sağlayın.** Bu yaklaşımda, önbelleğe alınan verileri veya varsayılan değeri döndürme gibi bir istek başarısız olduğunda istemci işlemi geri dönüş mantığı gerçekleştirir. Bu, sorgular için uygun bir yaklaşımdır ve güncelleştirmeler veya komutlar için daha karmaşıktır.

**Sıralanmış istek sayısını sınırlayın.** İstemci, istemci mikro hizmetinin belirli bir hizmete gönderebileceği bekleyen istek sayısına da üst sınır koymalı. Sınıra ulaşıldıysa, ek isteklerde bulunmak büyük olasılıkla anlamsızdır ve bu denemeler inhemen başarısız olmalıdır. Uygulama açısından, Polly [Bulkhead İzolasyon](https://github.com/App-vNext/Polly/wiki/Bulkhead) ilkesi bu gereksinimi karşılamak için kullanılabilir. Bu yaklaşım aslında uygulama olarak paralelleştirme <xref:System.Threading.SemaphoreSlim> azaltmadır. Ayrıca bölme dışında bir "kuyruk" izin verir. Yürütmeden önce bile proaktif olarak fazla yük dökebilirsiniz (örneğin, kapasite tam olarak kabul edildiği için). Bu, devre kesici hataları beklediğinden, belirli hata senaryolarına yanıtını bir devre kesicinin olabileceğinden daha hızlı yapar. [Polly'deki](http://www.thepollyproject.org/) BulkheadPolicy nesnesi, bölme ve sıranın ne kadar dolu olduğunu ortaya çıkarır ve otomatik yatay ölçekleme sağlamak için kullanılabilen taşma olayları sunar.

## <a name="additional-resources"></a>Ek kaynaklar

- **Esneklik desenleri**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Esneklik Ekleme ve Performansı Optimize Etme**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Bölme.** GitHub deposu. Polly politikası ile uygulama.\
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Azure için esnek uygulamalar tasarlama**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Geçici hata işleme**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Önceki](handle-partial-failure.md)
>[Sonraki](implement-retries-exponential-backoff.md)
