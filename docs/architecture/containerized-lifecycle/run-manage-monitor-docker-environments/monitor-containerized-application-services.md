---
title: Kapsayıcı uygulama hizmetlerini izleme
description: İzleme kapsayıcısı mimarilerinin bazı önemli yönlerini öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374448"
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcı uygulama hizmetlerini izleme

Birden çok kapsayıcıya ve mikro hizmetlere bölünen uygulamalar, tüm uygulamanın davranışını izlemek ve analiz etmek için bir yola sahip olmak açısından önemlidir.

## <a name="azure-monitor"></a>Azure İzleyici

[Azure izleyici](https://azure.microsoft.com/services/monitor/) , canlı uygulamanızı izleyen genişletilebilir bir analiz hizmetidir. Performans sorunlarını saptamanıza ve tanılamanıza ve hangi kullanıcıların uygulamanızla gerçekten ne yaptığını anlamanıza yardımcı olur. Hizmetlerinizin veya uygulamalarınızın performansını ve kullanılabilirliğini sürekli olarak iyileştirmenize yardımcı olmak amacıyla geliştiriciler için tasarlanmıştır. Azure Izleyici, şirket içinde veya bulutta barındırılan .NET, Java, Node.js ve diğer birçok platform gibi çok çeşitli platformlarda hem Web/Hizmetler hem de tek başına uygulamalarla birlikte çalışmaktadır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure Izleyici 'ye Genel Bakış** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights nedir?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Azure Izleyici ölçümleri nedir?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Azure Izleyici 'de kapsayıcı Izleme çözümü** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Güvenlik ve yedekleme hizmetleri

Uygulamalarınızın ve altyapınızın iş ihtiyaçlarını desteklemeye yönelik en önemli koşullarda ve bu durumun mikro hizmetler alanında daha karmaşık hale gelmesi için işlem yapmanız gereken çok fazla ayrıntı desteği vardır. bu nedenle, işlem yapmanız gerektiğinde hem yüksek düzeyde hem de ayrıntılı görünümlere sahip olmak için bir yönteme ihtiyacınız vardır.

Azure, hem bulut hem de şirket içi kaynaklarınızın dört kritik yönünü yönetmek ve sunmak için araçlara sahiptir:

- **Güvenlik**. [Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/)ile.
  - Sanal makinelerinizin, uygulamalarınızın ve iş yüklerinizin güvenliği üzerinde tam görünürlük ve denetim sağlayın.
  - Güvenlik ilkelerinizin yönetimini merkezileştirin ve var olan işlem ve araçları tümleştirin.
  - Gelişmiş analiz ile gerçek tehditleri algılayın.

- **Yedekleme**. [Azure Backup](https://azure.microsoft.com/services/backup/).
  - Maliyetli iş kesintilerini önleyin, uyumluluk hedeflerini karşılayın ve verilerinizi fidye ve insan hatalarına karşı koruyun.
  - Yedekleme verilerinizi, iletim sırasında ve bekleyen zamanda şifreli tutun.
  - Yetkisiz kullanımı engellemek için çok faktörlü kimlik doğrulamasına göre erişim sağlayın.

- **Şirket içi kaynaklar**. [Karma bulut çözümleri](https://azure.microsoft.com/solutions/hybrid-cloud-app/)ile.

>[!div class="step-by-step"]
>[Önceki](manage-production-docker-environments.md) 
> [Sonraki](../key-takeaways/index.md)
