---
title: Bulut için hazırlık dayanıklı Hizmetleri oluşturun. Buluttaki geçici hataları benimseme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulut için hazırlık dayanıklı Hizmetleri oluşturun. Buluttaki geçici hataları benimseme
ms.date: 04/30/2018
ms.openlocfilehash: e6fae8140b55cb0308dca9f4b77e961501b41f8f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739403"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Bulut için hazırlayın dayanıklı hizmetler oluşturun: bulutta geçici olmayan sorunları açma

Dayanıklılık, hatalardan kurtulmakta ve çalışmaya devam edebilmesidir. Dayanıklılık, hatalardan kaçınma, ancak hataların gerçekleşmesi ve sonra kapalı kalma süresini veya veri kaybını önleyen bir şekilde yanıt vermeyi kabul eder. Dayanıklılık amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.

Uygulamanız, en azından donanım tabanlı bir model yerine yazılım tabanlı bir dayanıklılık modeli uyguladığı zaman bulut için hazırlayın. Bulut uygulamanız, kesinlikle ortaya çıkabilecek kısmi hataların ayracına sahip olmalıdır. Beklenen kısmi hatalarla dayanıklılık elde etmek için uygulamanızı tasarlayın veya kısmen yeniden düzenleyin. Geçici ağ kesintileri ve düğümleri gibi kısmi arızalarla veya bulutta kilitlenen VM 'Ler ile sanal makinelere yönelik olarak tasarlanmalıdır. Bir Orchestrator kümesi içindeki farklı bir düğüme taşınmakta olan kapsayıcılar bile uygulama içinde aralıklı kısa hatalara neden olabilir.

## <a name="handling-partial-failure"></a>Kısmi hata işleme

Bulut tabanlı bir uygulamada, kısmen hatalı bir risk var. Örneğin, tek bir Web sitesi örneği veya kapsayıcısı başarısız olabilir ya da kısa bir süre için kullanılamayabilir veya yanıt veremez olabilir. Ya da tek bir VM veya sunucu kilitlenebilir.

İstemciler ve hizmetler ayrı süreçler olduğundan, bir hizmet istemci isteğine zamanında yanıt veremeyebilir. Hizmet aşırı yüklenmiş ve isteklere yavaş yanıt verebilir ya da ağ sorunları nedeniyle kısa bir süredir erişilebilir olmayabilir.

Örneğin, Azure SQL veritabanı 'nda bir veritabanına erişen tek parçalı bir .NET uygulaması düşünün. Azure SQL veritabanı veya başka bir üçüncü taraf hizmeti kısa bir süre yanıt vermezse (bir Azure SQL veritabanı farklı bir düğüme veya sunucuya taşınabilir ve birkaç saniye boyunca yanıt vermeyebilir), Kullanıcı herhangi bir işlem gerçekleştirmeye çalıştığında, uygulama kilitlenebilir ve gösterebilir aynı anda bir özel durum w.

HTTP Hizmetleri kullanan bir uygulamada benzer bir senaryo meydana gelebilir. Kısa, geçici bir başarısızlık sırasında ağ veya hizmetin kendisi bulutta bulunmayabilir.

Şekil 4-9 ' de gösterildiği gibi dayanıklı bir uygulama, uygulamaya kaynakların geçici başarısızlıklarını işleme fırsatı vermek için "üstel geri alma ile yeniden denemeler" gibi teknikler uygulamalıdır. Ayrıca, uygulamalarınızda "devre kesiciler" kullanmanız gerekir. Devre kesici, bir uygulamanın bir kaynağa erişmeye çalışmayı, aslında uzun süreli bir hata oluştuğunda sonlandırır. Uygulama, devre kesici kullanarak bir hizmet reddine izin vermez.

![Üstel geri alma ile yeniden denemeler tarafından işlenen kısmi hataların diyagramı.](./media/build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud/retry-partial-failures.png)

**Şekil 4-9.** Üstel geri alma ile yeniden denemeler tarafından işlenen kısmi arızalar

Bu teknikleri, hem HTTP kaynaklarında hem de veritabanı kaynaklarında kullanabilirsiniz. Şekil 4-9 ' de, uygulama 3 katmanlı bir mimariye dayanır, bu nedenle hizmet düzeyinde (HTTP) ve veri katmanı düzeyinde (TCP) Bu tekniklerin olması gerekir. Veritabanına ek olarak yalnızca tek bir uygulama katmanını kullanan tek parçalı bir uygulamada (ek hizmet veya mikro hizmet olmadan), veritabanı bağlantı düzeyindeki geçici hataların işlenmesi yeterli olabilir. Bu senaryoda, veritabanı bağlantısının yalnızca belirli bir yapılandırması gerekir.

Kullandığınız .NET sürümüne bağlı olarak veritabanına erişen dayanıklı iletişimler uygularken, bu, basit olabilir (örneğin, [Entity Framework 6 veya üzeri ile](/ef/ef6/fundamentals/connection-resiliency/retry-logic)). Veritabanı bağlantısını yapılandırmanın yalnızca bir önemi vardır. Ya da, [geçici hata Işleme uygulama bloğu](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (.net 'in önceki sürümleri için) gibi ek kitaplıklar kullanmanız veya kendi kitaplığınızı uygulamanız gerekebilir.

HTTP yeniden denemeleri ve devre kesicileri uygularken .NET önerisi, .NET Core desteği içeren .NET Framework 4,0, .NET Framework 4,5 ve .NET Standard 1,1 ' i hedefleyen [Polly](https://github.com/App-vNext/Polly) kitaplığı kullanmaktır.

Buluttaki kısmi hataların işlenmesine yönelik stratejileri nasıl uygulayacağınızı öğrenmek için aşağıdaki başvurulara bakın.

### <a name="additional-resources"></a>Ek kaynaklar

- **Kısmi başarısızlığı işlemek için esnek iletişim uygulama**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework bağlantı dayanıklılığı ve yeniden deneme mantığı (sürüm 6 ve üzeri)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Geçici hata Işleme uygulama bloğu**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Esnek HTTP iletişimi için Polly kitaplığı**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[İleri](modernize-your-apps-with-monitoring-and-telemetry.md)
