---
title: "Bulut için hazır dayanıklı Hizmetleri oluşturun. Bulutta geçici hataları çekirdeğin"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bulut için hazır dayanıklı Hizmetleri oluşturun. Bulutta geçici hataları çekirdeğin"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 9c21ae37ad2e4fc318eb4b206069db7662bfc5d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Bulut için hazır dayanıklı Hizmetleri yapı: çekirdeğin bulutta geçici hataları 

Dayanıklılık, arızalardan kurtarmak ve çalışmaya devam yeteneğidir. Dayanıklılık hatalarını önleme ancak hataları oluşur olgu kabul ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt ilgili değildir. Dayanıklılık bir hatadan sonra uygulamaya tam çalışır bir duruma geri dönmek için hedefidir.

Yazılım tabanlı bir model dayanıklılık yerine bir donanım tabanlı modeli en azından, bunu uygulayan uygulamanızı bulut için hazır olur. Bulut uygulamanızı kesinlikle oluşacaktır kısmi hataları çekirdeğin gerekir. Tasarım veya kısmen beklenen kısmi hataları dayanıklılık elde etmek istiyorsanız, uygulamanızın yeniden düzenlemeniz gerekir. Geçici ağ kesintileri ve düğümler ya da bulutta kilitlenen VM'ler gibi kısmi hatalarıyla başa çıkacak şekilde tasarlanmalıdır. Bir orchestrator kümedeki farklı bir düğüme taşınmasını bile kapsayıcıları, uygulama içinde aralıklı kısa hatalarına neden olabilir.

## <a name="handling-partial-failure"></a>Kısmi hata işleme

Bulut tabanlı bir uygulama içinde ever-present bir kısmi başarısızlık riskini yoktur. Örneğin, tek bir Web sitesi örneği veya bir kapsayıcı başarısız olabilir veya kullanılamayabilir veya kısa bir süre için yanıt olabilir. Veya tek bir VM veya sunucu kilitlenmesine neden olabilir.

İstemcileri ve Hizmetleri ayrı işlemler olduğundan, bir hizmet bir istemcinin isteğine zamanında yanıt mümkün olmayabilir. Hizmet aşırı yüklenmiş ve son derece yavaş isteklerine yanıt ya da onu yalnızca ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir.

Örneğin, Azure SQL veritabanındaki bir veritabanına erişir tek yapılı bir .NET uygulaması göz önünde bulundurun. Azure SQL veritabanı veya başka bir üçüncü taraf hizmet için kısa bir yanıt vermiyorsa (bir Azure SQL veritabanı farklı bir düğüme veya sunucuya taşınması ve birkaç saniye süreyle yanıt vermeyen) süresi, kullanıcı herhangi bir işlem yapmaya çalıştığında, uygulamanın kilitlenmesine neden olabilir ve Göster w çok aynı anda bir özel durum.

Benzer Senaryo HTTP Hizmetleri kullanan bir uygulama ortaya çıkabilir. Ağ veya hizmet bulutta sırasında kısa, geçici bir hata kullanılamayabilir.

Şekil 4-9'gösterilene benzer esnek bir uygulama, uygulama kaynaklarında geçici hataları işlemek için Fırsat vermek için "üstel geri alma ile yeniden deneme" gibi teknikler uygulamanız gerekir. Ayrıca, uygulamalarınızda "hattı ayırıcıları" kullanmanız gerekir. Devre kesici gerçekte uzun vadeli bir hataya olduğunda bir kaynağa erişmeye çalışırken bir uygulamanın durdurur. Devre kesici kullanarak, uygulamanın kendisinin hizmet reddi provoking önler.

![Yeniden deneme üstel geri alma ile tarafından işlenen kısmi hataları](./media/image9.png)

> **Şekil 4-9.** Yeniden deneme üstel geri alma ile tarafından işlenen kısmi hataları

Bu teknikler, hem HTTP kaynakları ve veritabanı kaynaklarını kullanabilirsiniz. Bu nedenle bu teknikler Hizmetleri düzeyi (HTTP) ve veri katmanı düzeyinde (TCP) gerekir Şekil 4-9'da 3 katmanlı mimarisi uygulama temel alır. İçinde yalnızca bir tek uygulama katmanı veritabanı (ek hizmetler veya mikro) ek olarak kullanan tek yapılı bir uygulamayı, veritabanı bağlantı düzeyinde geçici hataları işleme yeterli olabilir. Bu senaryoda, genellikle yalnızca belirli bir yapılandırma veritabanı bağlantısı gereklidir.

Kullanmakta olduğunuz, .NET sürümüne bağlı olarak veritabanına erişmek dayanıklı iletişimleri uygularken çok basit olabilir (örneğin, [Entity Framework 6 veya sonrası](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), bu yapılandırma yalnızca bir konudur veritabanı bağlantı). Veya gibi ek kitaplıklara kullanmanız gerekebilir [geçici hata işleme uygulama bloğu](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (önceki sürümleri için .NET), veya hatta kendi kitaplığı uygulamalıdır.

HTTP yeniden deneme ve hattı ayırıcıları uygularken, .NET için kullanmanız önerilir [Polly](https://github.com/App-vNext/Polly) .NET 4.0, .NET 4.5 ve .NET Core desteği içeren .NET standart 1.1, hedefler kitaplığı.

Bulutta kısmi hataları işlemek için stratejilerini uygulamak üzere öğrenmek için aşağıdaki kaynaklara bakın.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Kısmi hata işlemek için esnek iletişimi uygulama**

    [https://docs.microsoft.com/dotnet/Standard/microservices-Architecture/implement-resilient-Applications/partial-failure-Strategies](https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies)

-   **Entity Framework bağlantı dayanıklılık ve yeniden deneme mantığı (sürüm 6 ve üzeri)**

    [https://msdn.microsoft.com/en-us/library/dn456835 (v=vs.113).aspx](https://msdn.microsoft.com/en-us/library/dn456835(v=vs.113).aspx)

-   **Geçici hata işleme uygulama bloğu**

<!-- -->

-   [https://msdn.microsoft.com/en-us/library/hh680934 (v=pandp.50).aspx](https://msdn.microsoft.com/en-us/library/hh680934(v=pandp.50).aspx)

-   **Esnek HTTP iletişimi için Polly kitaplığı**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[sonraki](modernize-your-apps-with-monitoring-and-telemetry.md)
