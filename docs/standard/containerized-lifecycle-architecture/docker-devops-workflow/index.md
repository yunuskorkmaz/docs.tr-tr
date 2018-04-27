---
title: Microsoft araçları ile docker uygulama devops iş akışı
description: Microsoft araçları ile Microsoft Platformu ve Toolsdevops akışıyla kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bde96fd6348cf651dcca988eb546549fedf4df85
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft araçları ile docker uygulama DevOps iş akışı

Microsoft Visual Studio, Visual Studio Team Services, Team Foundation Server ve Application Insights geliştirme ve takım projeleri yönetme ve hızlı bir şekilde derleme, test ve dağıtmak için Araçlar verir BT işlemleri için kapsamlı bir ekosistem sağlayın Kapsayıcılı uygulamalar.

Visual Studio ve Team Foundation Server şirket yanı sıra bulut Visual Studio Team Services ile geliştirme ekipleri üretken derleme, test ve herhangi bir platformda doğru (Windows veya Linux) yönlendirilmiş kapsayıcılı uygulamaları bırakın.

Microsoft araçları ardışık düzen kapsayıcılı uygulamaların belirli uygulamaları için otomatik hale getirebilirsiniz — Docker, .NET Core veya diğer platformlar ile herhangi bir birleşimini — genel yapılar ve sürekli tümleştirme (CI) ve Visual Studio Team Services ile testleri veya Team Foundation Server için sürekli dağıtım (CD) Docker ortamlara (hazırlama, geliştirme, üretim) ve Application Insights ile geliştirme ekibi hizmetlere analytics bilgilerini iletmek için. Her kod tamamlama Hizmetleri belirli kapsayıcılı ortamları (CD) otomatik olarak dağıtmak ve bir yapı (CI) başlatın.

Geliştiriciler ve sınayıcılar hızla ve kolayca Docker üzerinde Microsoft Azure'da şablonları kullanarak bağlı üretim benzeri geliştirme ve test ortamları sağlayabilirsiniz.

Kapsayıcılı uygulama geliştirme karmaşıklığını sürekli olarak iş karmaşıklık ve ölçeklenebilirlik gereksinimlerine bağlı olarak artırır. Bu iyi bir örneği olan mikro mimarileri üzerinde tabanlı uygulamalar. Bu tür bir ortamda başarılı olması için projenizi tüm yaşam döngüsünü otomatikleştirmek — yalnızca derleme ve dağıtım, ancak telemetri koleksiyonunu birlikte sürümleri de yönetmeniz gerekir. Visual Studio Team Services ve Azure aşağıdaki yetenekleri sağlar:

-   Visual Studio Team Services/Team Foundation Server kaynak kodu Yönetimi (Git veya Team Foundation sürüm denetimi göre), Çevik planlama (Çevik, Scrum ve CMMI desteklenir), CI, yayın yönetimi ve diğer araçları Çevik ekipler için.

-   Visual Studio Team Services/Team Foundation Server ile kolayca bir CI, derleme, test, teslim oluşturmak ve mikro hizmetler için yönetim potansiyel yayın ilk ve üçüncü taraf uzantıları güçlü ve artan bir ekosistemi içerir.

-   Visual Studio Team Services yapı ardışık düzeninize bir parçası olarak otomatikleştirilmiş testleri çalıştırma.

-   Visual Studio Team Services sıkılaştırabilirsiniz DevOps yaşam döngüsü üretim ortamları için değil, ancak ayrıca test, birden çok ortamlara teslimin A dahil olmak üzere / B deneme, [yalancı sürümleri](https://martinfowler.com/bliki/CanaryRelease.html)ve benzeri.

-   Kuruluşlar kolayca hazırlayabilirsiniz Docker kapsayıcıları (veri, PaaS, vb.) Azure bileşenleri bağımlılıkları yanı sıra Azure kapsayıcı kayıt defterinde depolanan özel görüntülerden oldukları zaten araçlarıyla Azure Resource Manager şablonları kullanma rahat çalışma.


>[!div class="step-by-step"]
[Önceki] (.. / design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [sonraki] (docker-application-outer-loop-devops-workflow.md)
