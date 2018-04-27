---
title: Microsoft teknolojileri bulut devops kullanılmaya hazır uygulamalar
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Microsoft teknolojileri bulut DevOps çapında kullanılmaya hazır uygulamalar
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d3a0572b833a4ca3be1db3b3b531a76ca34fe4ab
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-technologies-in-cloud-devops-ready-applications"></a>Microsoft teknolojileri bulut devops kullanılmaya hazır uygulamalar

Aşağıdaki liste, Araçlar, teknolojileri ve bulut DevOps kullanılmaya hazır uygulamalar gereksinim olarak kabul edilen çözümleri açıklar. Bulut DevOps kullanılmaya hazır uygulamalar önceliklerinizden bağlı olarak seçerek veya yavaş yavaş benimseyebilirsiniz.

-   **Bulut altyapısı**: işlem platformu, işletim sistemi, ağ ve depolama alanı sağlar altyapı. Microsoft Azure bu düzeyde konumlandırıldı.

-   **Çalışma zamanı**: Bu katmanda uygulamayı çalıştırmak için bir ortam sağlar. Kapsayıcıları kullanıyorsanız, bu katman, genellikle dayanır [Docker altyapısına](https://docs.docker.com/engine/)Linux ana bilgisayarlarda veya Windows konakları üzerinde çalışıyor. ([Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) ile Windows Server 2016'dan başlayarak desteklenmektedir. Windows kapsayıcılar olan en iyi seçenek Windows üzerinde çalışan var olan .NET Framework uygulamaları için.)

-   **Yönetilen bulut**: yönetilen bir bulut seçeneği seçtiğinizde, gider ve ağ yapılandırmasını yönetmek ve temel altyapı, sanal makineleri, işletim sistemi yamalarını destekleme karmaşıklığını önleyebilirsiniz. Iaas kullanarak geçirmek seçerseniz, ilişkili maliyetler ve bu görevlerin tümü için sorumlu. Yönetilen bir bulut seçenekte, yalnızca uygulamalar ve geliştirme hizmetler yönetin. Bulut hizmeti sağlayıcısı genellikle şey yönetir. Azure yönetilen bulut Hizmetleri'nde örneklerindendir [Azure SQL veritabanı](https://azure.microsoft.com/services/sql-database), [Azure Redis önbelleği](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure veritabanı için MySQL](https://azure.microsoft.com/services/mysql/), [Azure veritabanı PostgreSQL için](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)ve yönetilen gibi işlem hizmetlerini [VM ölçek Ayarlar](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [Azure App Service](https://azure.microsoft.com/services/app-service/), ve [Azure kapsayıcı hizmeti](https://azure.microsoft.com/services/container-service/).

-   **Uygulama geliştirme**: kapsayıcılarında çalışan uygulamaları derlerken çok sayıda dillerden seçebilirsiniz. Bu kılavuzda, biz odaklanmak [.NET](https://www.microsoft.com/net), ancak Node.js, Python, gibi diğer diller kullanarak kapsayıcı tabanlı uygulamalar geliştirebilir yay/Java ya da GoLang.

-   **İzleme, günlüğe kaydetme ve denetim telemetri**: izleme ve denetim uygulamaları ve bulutta çalışan kapsayıcılar yeteneği bulut DevOps-hazır bir uygulama için kritik öneme sahiptir. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) ve [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) izleme ve denetim için bulut DevOps kullanılmaya hazır uygulamalar sağlayan ana Microsoft araçlardır.

-   **Sağlama**: Otomasyon araçları, altyapı sağlamak ve birden çok ortamlara (üretim, test, hazırlık) bir uygulama dağıtmanıza yardımcı. Bir uygulamanın yapılandırma ve ortamını yönetmek için Chef ve Puppet gibi araçlar kullanın. Bu katman, aynı zamanda daha basit ve daha doğrudan yaklaşımlar kullanılarak uygulanabilir. Örneğin, doğrudan Azure komut satırı araçları, arabirimi (Azure CLI) kullanarak dağıtın ve sonra sürekli dağıtım kullanın ve yönetim ardışık düzenlerinde yayın [Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Uygulama yaşam döngüsü**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/) ve Jenkins gibi başka araçlar yardımcı derleme otomasyon sunucuları CI/CD ardışık düzen, yayın yönetimi dahil olmak üzere uygulama.

Bu bölümde ve ilgili izlenecek yollar, sonraki bölümlerde özellikle çalışma zamanı katman (Windows kapsayıcıları) hakkındaki ayrıntıları odaklanır. Kılavuzu, Windows Server 2016 (ve sonraki sürümler) Windows kapsayıcılarında VM'ler dağıtma yöntemleri açıklar. Azure Service Fabric, Kubernetes ve Azure kapsayıcı hizmeti gibi daha gelişmiş orchestrator Katmanlar ele alınmaktadır. Orchestrator Katmanlar ayarlama (Windows tabanlı) var olan .NET Framework uygulamaları bulut DevOps çapında kullanılmaya hazır uygulamalar olarak modernizing için temel bir gereksinimdir.

## <a name="monolithic-applications-can-be-cloud-devops-ready"></a>Tek yapılı uygulamaları *yapabilirsiniz* buluta DevOps hazır olun

Tek yapılı uygulamaların (mikro üzerinde dayalı olmayan uygulamalar) vurgulamak önemlidir *yapabilirsiniz* bulut DevOps çapında kullanılmaya hazır uygulamalar olabilir. Yapı ve model kapsayıcıları, kesintisiz teslim ve DevOps bir bileşimini kullanarak bulut yararlanmak tek yapılı uygulamaları çalıştırmak. Varolan bir tek yapılı uygulama için iş hedeflerinize doğru ise, onu modernize ve bulut DevOps kullanıma hazır hale getirebilirsiniz.

Benzer şekilde, tek yapılı uygulamaları bulut DevOps çapında kullanılmaya hazır uygulamalar olabiliyorsa, N katmanlı uygulamalar gibi diğer, daha karmaşık mimarileri bulut DevOps çapında kullanılmaya hazır uygulamalar da modernized.

>[!div class="step-by-step"]
[Önceki](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)
[sonraki](what-about-cloud-optimized-applications.md)
