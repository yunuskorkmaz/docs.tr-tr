---
title: Microsoft araçları ile Docker uygulaması DevOps iş akışı
description: Microsoft araçları ile Microsoft platformu ve araçları DevOps iş akışı ile Kapsayıcılı Docker uygulaması yaşam döngüsü
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295744"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft araçları ile Docker uygulaması DevOps iş akışı

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server ve Azure Izleyici, ekibinize projeleri yönetmek için Araçlar veren ve Kapsayıcılı oluşturma, test etme ve dağıtma gibi geliştirme ve BT işlemleri için kapsamlı bir ekosistem sağlar uygulamaları.*

Visual Studio ve Bulutta Azure DevOps Services, şirket içi Team Foundation Server birlikte, geliştirme ekipleri Windows veya Linux 'u hedefleyen Kapsayıcılı uygulamaları verimli bir şekilde oluşturabilir, test edebilir ve serbest bırakabilir.

Microsoft araçları, genel derlemeler ve sürekli tümleştirme (CI) ve Azure DevOps Services veya ekiple testlerin yanı sıra, Kapsayıcılı uygulamaların belirli uygulamaları (Docker, .NET Core veya diğer platformlarla birlikte) için işlem hattını otomatikleştirebilir. Azure Izleyici aracılığıyla, temel sunucu, Docker ortamlarına (geliştirme, hazırlama, üretim) ve hizmetler hakkındaki analiz bilgilerini geliştirme ekibine iletme. Her kod yürütmesi bir yapı (CI) başlatabilir ve hizmetleri otomatik olarak belirli Kapsayıcılı ortamlara (CD) dağıtır.

Geliştiriciler ve test ediciler, Microsoft Azure şablonlar kullanarak, Docker tabanlı üretim geliştirme ve test ortamlarını kolayca ve hızlı bir şekilde sağlayabilir.

Kapsayıcılı uygulama geliştirmenin karmaşıklığı, iş karmaşıklığı ve ölçeklenebilirlik gereksinimlerine bağlı olarak artmasıyla artar. Bu karmaşıklığa yönelik iyi bir örnek, mikro hizmet mimarilerine dayalı uygulamalardır. Bu tür bir ortamda başarılı olmak için, projeniz yalnızca derleme ve dağıtım değil tüm yaşam döngüsünü otomatikleştirmelidir, ancak aynı zamanda sürümleri telemetri koleksiyonuyla birlikte yönetmelidir. Azure DevOps Services ve Azure aşağıdaki özellikleri sunar:

- Azure DevOps Services/Team Foundation Server kaynak kodu yönetimi (git veya Team Foundation Sürüm Denetimi tabanlı), çevik planlama (çevik, Scrum ve CMMı desteklenir), CI, Release Management ve Çevik takımlar için diğer araçlar.

- Azure DevOps Services ve Team Foundation Server, mikro hizmetler için kolayca CI, derleme, test, teslim ve sürüm yönetimi işlem hattı oluşturabileceğiniz birinci ve üçüncü taraf genişletmenin güçlü ve büyüyen bir ekosistemini içerir.

- Azure DevOps Services içinde derleme işlem hattınızı bir parçası olarak otomatikleştirilmiş testler çalıştırın.

- Azure DevOps Services DevOps yaşam döngüsünü yalnızca üretim ortamları için değil, aynı zamanda bir/B deneme, [kanarya](https://martinfowler.com/bliki/CanaryRelease.html)ve benzeri gibi test için değil, birden çok ortama gönderim ile açabilir.

- Kuruluşlar, Azure Container Registry ' de depolanan özel görüntülerden (veri, PaaS, vb.), zaten rahat olan araçlarla Azure Resource Manager şablonları kullanarak Azure bileşenleri (Data, PaaS vb.) ile birlikte her türlü bağımlılıktan Docker Kapsayıcıları sağlayabilir.

>[!div class="step-by-step"]
>[Önceki](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)İleri
>[](docker-application-outer-loop-devops-workflow.md)
