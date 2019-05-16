---
title: Microsoft araçları ile Docker uygulaması DevOps iş akışı
description: Microsoft araçları ile Microsoft Platformu ve araçları DevOps iş akışı ile kapsayıcı Docker uygulaması yaşam döngüsü
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644817"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft araçları ile Docker uygulaması DevOps iş akışı

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server ve Azure İzleyici kapsamlı bir ekosistem, geliştirme ve takım projeleri yönetme ve hızlı bir şekilde oluşturun, araçları sunun BT işlemleri test etmek ve dağıtmak için kapsayıcılı hale sağlayın uygulamalar.*

Visual Studio ve Azure DevOps hizmetleriyle birlikte Team Foundation Server şirket içi, bulut geliştirme ekipleri üretken bir şekilde derleme, test ve hedefleyen Windows veya Linux'ta kapsayıcılı uygulamaları yayınlayın.

Microsoft araçları kapsayıcılı uygulamaların belirli uygulamalar için ardışık düzenini otomatik hale getirebilirsiniz: Docker, .NET Core ve diğer platformlarla herhangi bir birleşimini — genel yapılar ve sürekli tümleştirme (CI) ve Azure DevOps Services veya Team ile testleri Foundation Server için sürekli dağıtım (CD) Docker ortamlarını (hazırlama, geliştirme, üretim) ve Hizmetleri Azure İzleyici aracılığıyla Geliştirme ekibine hakkında analytics bilgi aktarmak için. Her kod işlemesinde bir derleme (CI) başlatabilir ve Hizmetleri belirli kapsayıcılı ortamlara (CD) otomatik olarak dağıtır.

Geliştiricilere ve test edicilere kolayca ve hızlı bir şekilde Microsoft Azure'da şablonları kullanarak Docker tabanlı üretim ortamına benzer geliştirme ve test ortamları sağlayabilirsiniz.

Kapsayıcılı uygulama geliştirme karmaşıklığını iş karmaşıklığını ve ölçeklenebilirlik gereksinimlerine bağlı olarak giderek artar. Mikro hizmet mimarileri üzerinde tabanlı uygulamaları bu karmaşıklığı iyi bir örneği var. Bu tür bir ortamda başarılı olmak için projeniz tüm yaşam döngüsünü otomatikleştirin — yalnızca derleme ve dağıtım, ancak telemetri koleksiyonunu birlikte sürümleri de yönetmeniz gerekir. Azure DevOps hizmetler ve Azure aşağıdaki özellikleri sunar:

- Azure DevOps Hizmetleri/Team Foundation Server kaynak kodu Yönetimi (Git veya Team Foundation sürüm denetimi göre), Çevik planlama (Agile, Scrum ve CMMI desteklenir), CI, sürüm yönetimi ve Çevik ekipler için diğer araçlar.

- Azure DevOps Hizmetleri ve Team Foundation Server ile kolayca oluşturun, CI, derleme, test, teslim ve yayın Yönetimi işlem mikro hizmetlere yönelik birinci ve üçüncü taraf uzantıları güçlü ve giderek büyüyen bir ekosistemi içerir.

- Azure DevOps Hizmetleri'nde, derleme işlem hattı bir parçası olarak otomatik testler çalıştırın.

- Azure DevOps hizmetleriyle sıkılaştıran üretim ortamları için değil, aynı zamanda test, DevOps yaşam döngüsü ile birden çok ortama teslim A dahil olmak üzere / B deneme [kanarya sürümleri](https://martinfowler.com/bliki/CanaryRelease.html)ve benzeri.

- Kuruluşların kolayca sağlayabilirsiniz (veri, PaaS, vb.) Azure bileşenlerini bağımlılığın yanı sıra Azure Container Registry'de depolanan özel görüntülerden Docker kapsayıcıları, zaten alışık araçları ile Azure Resource Manager şablonlarını kullanarak.

>[!div class="step-by-step"]
>[Önceki](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[İleri](docker-application-outer-loop-devops-workflow.md)
