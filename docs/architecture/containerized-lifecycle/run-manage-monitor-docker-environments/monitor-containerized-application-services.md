---
title: Kapsayıcı uygulama hizmetlerini izleme
description: Konteyner mimarilerini izlemenin bazı önemli yönlerini öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295621"
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcı uygulama hizmetlerini izleme

Tüm uygulamanın davranışını izlemek ve analiz etmek için birden çok kapsayıcıya ve mikro hizmetlere bölünmüş uygulamalar için çok önemlidir.

## <a name="azure-monitor"></a>Azure İzleyici

[Azure Monitor,](https://azure.microsoft.com/services/monitor/) canlı uygulamanızı izleyen genişletilebilir bir analiz hizmetidir. Performans sorunlarını algılamanıza ve tanılamanıza ve kullanıcıların uygulamanızla gerçekte ne yaptığını anlamanıza yardımcı olur. Hizmetlerinizin veya uygulamalarınızın performansını ve kullanılabilirliğini sürekli olarak geliştirmenize yardımcı olmak amacıyla geliştiriciler için tasarlanmıştır. Azure Monitor, .NET, Java, Node.js ve şirket içinde veya bulutta barındırılan diğer birçok platform gibi çok çeşitli platformlarda hem web/hizmetler hem de bağımsız uygulamalarla çalışır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure Monitörüne Genel Bakış** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights nedir?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Azure Monitör Ölçümleri nedir?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Azure Monitör'de Konteyner İzleme çözümü** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Güvenlik ve yedekleme hizmetleri

Uygulamalarınızın ve altyapınızın iş gereksinimlerini desteklemek için en üst düzey durumda olduğundan ve mikro hizmetler alanında durumun daha karmaşık hale gelmesiiçin, işlemeniz gereken birçok ayrıntıiçeren birçok destek işi vardır, bu nedenle harekete geçmeniz gerektiğinde hem üst düzey hem de ayrıntılı görünümlere sahip olabilirsiniz.

Azure, hem bulutunuzun hem de şirket içi kaynaklarınızın dört kritik yönünü yönetmek ve birleşik bir görünüm sağlamak için araçlara sahiptir:

- **Güvenlik**. [Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/)ile.
  - Sanal makinelerinizin, uygulamalarınızın ve iş yüklerinizin güvenliği üzerinde tam görünürlük ve denetim edinin.
  - Güvenlik politikalarınızın yönetimini merkezileştirin ve varolan süreç ve araçları entegre edin.
  - Gelişmiş analitikle gerçek tehditleri algılayın.

- **Yedek**. [Azure Yedekleme](https://azure.microsoft.com/services/backup/)ile .
  - Maliyetli iş aksaklıklarından kaçının, uyumluluk hedeflerini karşın ve verilerinizi fidye yazılımlarına ve insan hatalarına karşı koruyun.
  - Yedekleme verilerinizi aktarım sırasında ve istirahatte şifrelenmiş tutun.
  - Yetkisiz kullanımı önlemek için çok faktörlü kimlik doğrulamayı temel alan erişim sağlayın.

- **Şirket içi kaynaklar.** [Gerçekten tutarlı bir hibrid bulut](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)ile .

>[!div class="step-by-step"]
>[Önceki](manage-production-docker-environments.md)
>[Sonraki](../key-takeaways/index.md)
