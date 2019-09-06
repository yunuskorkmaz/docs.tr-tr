---
title: Kapsayıcı uygulama hizmetlerini izleme
description: İzleme kapsayıcısı mimarilerinin bazı önemli yönlerini öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295621"
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcı uygulama hizmetlerini izleme

Birden çok kapsayıcıya ve mikro hizmetlere bölünen uygulamalar, tüm uygulamanın davranışını izlemek ve analiz etmek için bir yola sahip olmak açısından önemlidir.

## <a name="azure-monitor"></a>Azure İzleyici

[Azure izleyici](https://azure.microsoft.com/services/monitor/) , canlı uygulamanızı izleyen genişletilebilir bir analiz hizmetidir. Performans sorunlarını saptamanıza ve tanılamanıza ve hangi kullanıcıların uygulamanızla gerçekten ne yaptığını anlamanıza yardımcı olur. Hizmetlerinizin veya uygulamalarınızın performansını ve kullanılabilirliğini sürekli olarak iyileştirmenize yardımcı olmak amacıyla geliştiriciler için tasarlanmıştır. Azure Izleyici, .NET, Java, Node. js gibi çok çeşitli platformlar ve şirket içinde veya bulutta barındırılan diğer birçok platform üzerinde hem Web/hizmet hem de tek başına uygulamalarla birlikte kullanılabilir.

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

Uygulamalarınızın ve altyapınızın iş ihtiyaçlarını desteklemeye yönelik en iyi çentik durumunda olduğundan emin olmak için işleyebilmeniz gereken çok sayıda ayrıntıyı destekler ve durum mikro hizmetler alanında daha karmaşık hale gelirse, işlem yapmanız gerektiğinde hem yüksek düzey hem de ayrıntılı görünümlere sahip olabilirsiniz.

Azure, hem bulut hem de şirket içi kaynaklarınızın dört kritik yönünü yönetmek ve sunmak için araçlara sahiptir:

- **Güvenlik**. [Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/)ile.
  - Sanal makinelerinizin, uygulamalarınızın ve iş yüklerinizin güvenliği üzerinde tam görünürlük ve denetim sağlayın.
  - Güvenlik ilkelerinizin yönetimini merkezileştirin ve var olan işlem ve araçları tümleştirin.
  - Gelişmiş analiz ile gerçek tehditleri algılayın.

- **Yedekleme**. [Azure Backup](https://azure.microsoft.com/services/backup/).
  - Maliyetli iş kesintilerini önleyin, uyumluluk hedeflerini karşılayın ve verilerinizi fidye ve insan hatalarına karşı koruyun.
  - Yedekleme verilerinizi, iletim sırasında ve bekleyen zamanda şifreli tutun.
  - Yetkisiz kullanımı engellemek için çok faktörlü kimlik doğrulamasına göre erişim sağlayın.

- **Şirket içi kaynaklar**. [Gerçek anlamda tutarlı bir karma bulutla](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Önceki](manage-production-docker-environments.md)İleri
>[](../key-takeaways/index.md)
