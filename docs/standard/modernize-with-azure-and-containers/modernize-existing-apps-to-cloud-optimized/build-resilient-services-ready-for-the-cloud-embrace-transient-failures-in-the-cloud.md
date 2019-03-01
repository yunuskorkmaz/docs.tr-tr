---
title: Bulut için hazır olan dayanıklı hizmetler oluşturun. Bulutta geçici hataları benimseyin
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Bulut için hazır olan dayanıklı hizmetler oluşturun. Bulutta geçici hataları benimseyin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 801d017457d1cdc3c8a495c8127b203380cb1d9e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971838"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Bulut için hazır olan dayanıklı hizmetler derleme: Bulutta geçici hataları benimseyin

Dayanıklılık, hatalardan kurtularak çalışmaya devam yeteneğidir. Dayanıklılık hakkında hatalarını önleme ancak hataları meydana gelir gerçeğini kabul eden ve ardından bunları kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt değil. Dayanıklılığın hedefi, bir hatadan sonra uygulamayı tam çalışır duruma getirmektir.

En az bir yazılım tabanlı modeli dayanıklılık yerine bir donanım tabanlı modeli uygular, uygulamanızın bulut için hazır olur. Bulut uygulamanızın kesinlikle oluşacak kısmi hataları benimseyin gerekir. Tasarım veya kısmen beklenen kısmi hatalarıyla dayanıklılığı sağlamak için uygulamanızı yeniden düzenleyin. Geçici ağ kesintileri ve düğümleri ya da bulutta kilitlenen VM'ler gibi kısmi hataları olan başa çıkacak şekilde tasarlanmalıdır. Bir orchestrator kümedeki farklı bir düğüme taşınmasını bile kapsayıcıları, uygulama içinde aralıklı kısa hatalarına neden olabilir.

## <a name="handling-partial-failure"></a>Kısmi hata işleme

Bulut tabanlı bir uygulama içinde bir ardı arkası kısmi hata riskini yoktur. Örneğin, bir tek bir Web sitesi örneği veya bir kapsayıcı başarısız olabilir veya kullanılamıyor veya kısa bir süre için yanıt vermiyor olabilir. Alternatif olarak, tek bir VM veya sunucusuna kilitlenmesine neden olabilir.

Bir hizmet, istemciler ve hizmetler ayrı işlemler olduğundan, bir istemcinin isteğine zamanında yanıt vermek mümkün olmayabilir. Hizmet aşırı yüklenmiş ve yavaş isteklere yanıt ya da onu ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir.

Örneğin, bir veritabanını Azure SQL veritabanı'nda erişen tek parça bir .NET uygulaması göz önünde bulundurun. Azure SQL veritabanı veya başka bir üçüncü taraf hizmet için kısa bir yanıt vermiyorsa (bir Azure SQL veritabanı farklı bir düğüme veya sunucuya taşınması ve birkaç saniye süreyle yanıt vermiyor) zaman, herhangi bir işlem yapmak kullanıcı denediğinde, uygulama kilitlenebilir ve Göster w aynı anda bir özel durum.

Benzer bir senaryo, HTTP Hizmetleri kullanan bir uygulama ortaya çıkabilir. Bulutta sırasında kısa, geçici bir hata, ağ veya hizmet kullanılabilir olmayabilir.

Şekil 4-9'da gösterildiği gibi dayanıklı bir uygulama, uygulama kaynaklarında geçici hataları işlemek için bir fırsat vermek için "üstel geri alma ile yeniden" tekniklerle uygulamalıdır. Ayrıca, uygulamalarınızda "devre Kesiciler" kullanmanız gerekir. Devre kesici uzun vadeli bir hataya gerçekten olduğunda, bir kaynağa erişmeye çalışırken uygulamanın durdurur. Devre kesici kullanarak, uygulamanın kendisi için hizmet reddine provoking önler.

![Üstel geri alma ile yeniden tarafından işlenen kısmi hataları](./media/image9.png)

> **Şekil 4-9.** Üstel geri alma ile yeniden tarafından işlenen kısmi hataları

Bu teknikler HTTP kaynağı hem de veritabanı kaynaklarını kullanabilirsiniz. Böylece, bu teknikler Hizmetleri düzeyinde (HTTP) ve veri katmanı düzeyinde (TCP) Şekil 4-9'da uygulama 3 katmanlı mimarisini temel alır. Yalnızca bir tek uygulama katmanına ek (ek hizmet veya mikro hizmetler) veritabanı olarak kullanan tek parçalı bir uygulamada, veritabanı bağlantı düzeyinde geçici hataları işleme yeterli olabilir. Bu senaryoda, yalnızca belirli bir yapılandırma veritabanı bağlantısı gereklidir.

Kullanmakta olduğunuz, .NET sürümüne bağlı olarak veritabanına erişen dayanıklı iletişimleri uygularken basit olabilir (örneğin, [Entity Framework 6 veya sonrası](/ef/ef6/fundamentals/connection-resiliency/retry-logic). Bu, veritabanı bağlantısını yapılandırma adımlarından oluşur). Veya ek kitaplıklar gibi kullanmanız gerekebilir [geçici hata işleme uygulama bloğu](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (önceki sürümlerine yönelik .NET), veya hatta kendi kitaplığı uygulayın.

HTTP yeniden deneme ve devre Kesiciler uygularken, .NET için zamanlayıcısının [Polly](https://github.com/App-vNext/Polly) .NET Framework 4.0, .NET Framework 4.5 ve .NET standart, .NET Core desteği içeren 1.1 kitaplığı.

Bulutta kısmi hata işleme stratejileri uygulama hakkında bilgi edinmek için aşağıdaki kaynaklara bakın.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Kısmi hata işleme için dayanıklı iletişim uygulama**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   **Varlık çerçevesi bağlantı dayanıklılığı ve yeniden deneme mantığı (sürüm 6 ve üzeri)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

-   **Geçici hata işleme uygulama bloğu**

-   <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

-   **Polly kitaplığını dayanıklı HTTP iletişimi**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[İleri](modernize-your-apps-with-monitoring-and-telemetry.md)
