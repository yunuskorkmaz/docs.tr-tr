---
title: Kapsayıcı uygulama hizmetlerini izleme
description: Kapsayıcı mimarileri izleme bazı önemli noktalar öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641212"
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcı uygulama hizmetlerini izleme

Tüm uygulama davranışını çözümlemenize yarayan bir yol sağlamak bölme birden fazla kapsayıcılar ve mikro hizmet uygulamaları için önemlidir.

## <a name="azure-monitor"></a>Azure İzleyici

[Azure İzleyici](https://azure.microsoft.com/services/monitor/) Canlı uygulamanızı izler, bir genişletilebilir bir analiz hizmetidir. Performans sorunlarını algılayıp tanılamanıza ve kullanıcıların gerçekten uygulamanızla neler anlamak için yardımcı olur. Sürekli olarak performansını artırmak için yardımcı hedefi ve hizmet veya uygulamalardan birinde kullanılabilirliği içeren, geliştiricilere yönelik tasarlanmıştır. Azure İzleyici, .NET, Java, Node.js ve diğer birçok platformda şirket içinde barındırılan gibi platformlarda veya bulutta çeşitli uygulamalar web/hizmetleri ve tek başına ile çalışır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure İzleyicisi'ne genel bakış** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights nedir?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Azure İzleyici ölçümleri nedir?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Azure İzleyici'de kapsayıcı izleme çözümü** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Güvenlik ve yedekleme Hizmetleri

Çok bileşenli uygulamalar ve altyapı iş gereksinimlerini desteklemek için üstteki dişli durumda olduklarından emin olmak için işlemesine gerek ayrıntıları birçok destek işlerini vardır ve böylece, bir şekilde durum mikro hizmetler erişim, daha karmaşık hale gelir üst düzey ve ayrıntılı görünümlerini işlem yapması gerekir.

Azure, yönetmek ve hem bulut hem de şirket içi kaynaklar dört önemli yönlerini birleşik bir görünümünü sağlamak için geliştirme araçlarına sahiptir:

- **Güvenlik**. İle [Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/).
  - Sanal makineler, uygulamalarınızı ve iş yüklerinin güvenliğini üzerinde tam görünürlük ve denetim alın.
  - Güvenlik ilkelerinizin yönetimini merkezileştirin; mevcut işlemleri ve araçları tümleştirin.
  - Gelişmiş analiz sayesinde gerçek tehditleri algılayın.

- **Yedekleme**. İle [Azure yedekleme](https://azure.microsoft.com/services/backup/).
  - Maliyetli iş kesintilerinden kaçının, uyumluluk hedeflerinizi karşılayın ve verilerinizi fidye yazılımlarına ve insan hatalarına karşı koruyun.
  - Yedekleme verileriniz aktarımda ve bekleme sırasında şifrelenmiş tutun.
  - Yetkisiz kullanımı önlemek için çok faktörlü kimlik doğrulamasını temel alan erişim emin olun.

- **Şirket içi kaynaklara**. İle [tamamen tutarlı hibrit bulut](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Önceki](manage-production-docker-environments.md)
>[İleri](../key-takeaways/index.md)
