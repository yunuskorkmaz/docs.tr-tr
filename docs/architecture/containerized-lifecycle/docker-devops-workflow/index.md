---
title: Microsoft araçları ile Docker uygulaması DevOps iş akışı
description: Microsoft Platformu ve Tools DevOps iş akışı ile Microsoft araçları ile Containerized Docker Uygulama Yaşam Döngüsü
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295744"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft araçları ile Docker uygulaması DevOps iş akışı

*Microsoft Visual Studio, Azure DevOps Hizmetleri, Team Foundation Server ve Azure Monitor, ekibinize projeleri yönetmesi ve konteynerhaline getirilmiş araçları hızlı bir şekilde oluşturması, test etmesi ve dağıtması için kapsamlı bir geliştirme ve BT işlemleri için kapsamlı bir ekosistem sağlar Uygulama.*

Buluttaki Visual Studio ve Azure DevOps Hizmetleri ile birlikte Team Foundation Server şirket içinde geliştirme ekipleri, Windows veya Linux'u hedefleyen kapsayıcı laştırılmış uygulamaları verimli bir şekilde oluşturabilir, sınayabilir ve serbest bırakabilir.

Microsoft araçları, kapsayıcı laştırılmış uygulamaların belirli uygulamaları için ardışık denetimi otomatikleştirebilir (Docker, .NET Core veya diğer platformlarla herhangi bir kombinasyon—küresel yapılar ve Sürekli Tümleştirme (CI) ve Azure DevOps Hizmetleri veya Ekibi ile testler Foundation Server, Docker ortamlarına (Geliştirme, Evreleme, Üretim) sürekli dağıtım (CD) ve Azure Monitor aracılığıyla hizmetlerle ilgili analiz bilgilerini geliştirme ekibine iletmek için. Her kod commit bir yapı (CI) başlatabilir ve hizmetleri otomatik olarak belirli kapsayıcı ortamlara (CD) dağıtabilir.

Geliştiriciler ve sınayıcılar, Microsoft Azure'da şablonlar kullanarak Docker'a dayalı üretim benzeri geliştirme ve test ortamlarını kolayca ve hızlı bir şekilde sağlayabilir.

Konteynerleştirilmiş uygulama geliştirmenin karmaşıklığı, iş karmaşıklığına ve ölçeklenebilirlik gereksinimlerine bağlı olarak sürekli olarak artar. Bu karmaşıklığın iyi bir örneği mikrohizmet mimarilerine dayalı uygulamalardır. Böyle bir ortamda başarılı olmak için, projenizin yalnızca yapı ve dağıtım değil, aynı zamanda telemetri koleksiyonuyla birlikte sürümleri de yönetmesi gereken tüm yaşam döngüsünü otomatikleştirmesi gerekir. Azure DevOps Hizmetleri ve Azure aşağıdaki özellikleri sunar:

- Azure DevOps Services/Team Foundation Server kaynak kod yönetimi (Git veya Team Foundation Sürüm Denetimine dayalı), Çevik planlama (Çevik, Scrum ve CMMI desteklenir), CI, sürüm yönetimi ve Çevik takımlar için diğer araçlar.

- Azure DevOps Hizmetleri ve Team Foundation Server, mikro hizmetler için kolayca bir CI, inşa, test, teslimat ve sürüm yönetimi boru hattı oluşturabileceğiniz, birinci ve üçüncü taraf uzantılarından oluşan güçlü ve büyüyen bir ekosistem içerir.

- Azure DevOps Hizmetleri'nde yapı denetim sisteminizin bir parçası olarak otomatik testler çalıştırın.

- Azure DevOps Hizmetleri, DevOps yaşam döngüsünü sadece üretim ortamları için değil, aynı zamanda A/B denemeleri, [kanarya sürümleri](https://martinfowler.com/bliki/CanaryRelease.html)ve benzeri testler için birden fazla ortama teslim ederek sıkılaştırabilir.

- Kuruluşlar, Azure Kaynak Yöneticisi şablonlarını kullanarak Azure Kapsayıcı Kayıt Defteri'nde depolanan özel resimlerden Docker kapsayıcılarını ve azure bileşenlerine (Data, PaaS, vb.) zaten rahat oldukları araçları kullanarak kolayca sağlayabilir.

>[!div class="step-by-step"]
>[Önceki](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[Sonraki](docker-application-outer-loop-devops-workflow.md)
