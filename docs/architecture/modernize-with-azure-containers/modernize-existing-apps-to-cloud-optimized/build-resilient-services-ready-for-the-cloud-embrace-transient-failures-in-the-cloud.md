---
title: Bulut için hazır esnek hizmetler oluşturun. Buluttaki geçici hataları benimseme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Bulut için hazır esnek hizmetler oluşturun. Buluttaki geçici hataları benimseme
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711264"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Bulut için hazır olan dayanıklı hizmetler derleme: Bulutta geçici hataları kavrama

Esneklik, başarısızlıklardan kurtulma ve çalışmaya devam etme yeteneğidir. Esneklik, hatalardan kaçınmak değil, hataların oluşacağı gerçeğini kabul etmek ve ardından bunlara kapalı kalma süresini veya veri kaybını önleyecek şekilde yanıt vermektir. Esnekliğin amacı, bir hatadan sonra uygulamayı tam olarak işleyen bir duruma döndürmektir.

Uygulamanız, en azından donanım tabanlı bir model yerine yazılım tabanlı bir esneklik modeli uyguladığında bulut için hazırdır. Bulut uygulamanız, kesinlikle oluşacak kısmi hataları benimsemelidir. Beklenen kısmi hatalarda esneklik sağlamak için uygulamanızı tasarla veya kısmen yeniden düzenleme. Geçici ağ kesintileri ve düğümleri veya bulutta çöken VM'ler gibi kısmi hatalarla başa çıkacak şekilde tasarlanmalıdır. Bir orchestrator kümesi içinde farklı bir düğüme taşınan kapsayıcılar bile uygulama içinde aralıklı kısa hatalara neden olabilir.

## <a name="handling-partial-failure"></a>Kısmi hata işleme

Bulut tabanlı bir uygulamada, kısmi hata riski her zaman vardır. Örneğin, tek bir web sitesi örneği veya kapsayıcı başarısız olabilir veya kısa bir süre için kullanılamayabilir veya yanıt vermeyebilir. Veya, tek bir VM veya sunucu çökebilir.

İstemler ve hizmetler ayrı işlemler olduğundan, bir hizmet istemcinin isteğine zamanında yanıt veremeyebilir. Hizmet aşırı yüklenmiş ve isteklere yavaş yanıt verebilir veya ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir.

Örneğin, Azure SQL Veritabanı'ndaki bir veritabanına erişen yekpare bir .NET uygulamasını düşünün. Azure SQL veritabanı veya başka bir üçüncü taraf hizmeti kısa bir süre için yanıt vermiyorsa (Azure SQL veritabanı farklı bir düğüme veya sunucuya taşınabilir ve birkaç saniye yanıt vermeyebilir), kullanıcı herhangi bir işlem yapmaya çalıştığında uygulama çökebilir ve aynı anda bir özel durum gösterir.

BENZER bir senaryo, HTTP hizmetlerini tüketen bir uygulamada da oluşabilir. Kısa ve geçici bir hata sırasında ağ veya hizmetin kendisi bulutta kullanılamayabilir.

Şekil 4-9'da gösterilen gibi esnek bir uygulama, uygulamaya kaynaklardaki geçici hataları işlemek için bir fırsat vermek için "üstel geri tepme ile yeniden denemeler" gibi teknikler uygulamalıdır. Ayrıca uygulamalarınızda "devre kesiciler" kullanmalısınız. Devre kesici, uygulamanın aslında uzun vadeli bir hata olduğunda kaynağa erişmeye çalışmasından engeller. Bir devre kesici kullanarak, uygulama kendisine hizmet reddi provoke önler.

![Üstel geri tepme ile yeniden denemeler tarafından işlenen kısmi hataların diyagramı.](./media/retry-partial-failures.png)

**Şekil 4-9.** Üstel geri tepme ile yeniden denemeler tarafından işlenen kısmi hatalar

Bu teknikleri hem HTTP kaynaklarında hem de veritabanı kaynaklarında kullanabilirsiniz. Şekil 4-9'da uygulama 3 katmanlı bir mimariye dayanır, bu nedenle bu tekniklere hizmet düzeyinde (HTTP) ve veri katmanı düzeyinde (TCP) ihtiyaç duyarsınız. Veritabanına ek olarak yalnızca tek bir uygulama katmanı (ek hizmetler veya mikro hizmetler) kullanan yekpare bir uygulamada, veritabanı bağlantı düzeyinde geçici hataları işlemek yeterli olabilir. Bu senaryoda, veritabanı bağlantısının belirli bir yapılandırması gereklidir.

Kullandığınız .NET sürümüne bağlı olarak veritabanına erişen esnek iletişimleri uygularken, basit olabilir (örneğin, [Entity Framework 6 veya later ile.](/ef/ef6/fundamentals/connection-resiliency/retry-logic) Bu sadece veritabanı bağlantısını yapılandırma meselesi). Veya [Geçici Hata İşleme Uygulama Bloğu](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (.NET'in önceki sürümleri için) gibi ek kitaplıklar kullanmanız veya hatta kendi kitaplığınızı uygulamanız gerekebilir.

HTTP yeniden denemeleri ve devre kesicileri uygularken ,NET için öneri,.NET Framework 4.0, .NET Framework 4.5 ve .NET Standard 1.1'i hedefleyen [Polly](https://github.com/App-vNext/Polly) kitaplığını kullanmaktır.

Buluttaki kısmi hataları işleme stratejilerinin nasıl uygulanacağını öğrenmek için aşağıdaki başvurulara bakın.

### <a name="additional-resources"></a>Ek kaynaklar

- **Kısmi arızayı işlemek için esnek iletişimin uygulanması**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework bağlantı esnekliği ve yeniden deneme mantığı (sürüm 6 ve sonrası)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Geçici Hata İşleme Uygulama Bloğu**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Esnek HTTP iletişim için Polly kütüphanesi**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[Sonraki](modernize-your-apps-with-monitoring-and-telemetry.md)
