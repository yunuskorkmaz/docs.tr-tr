---
title: Bulut için iyileştirilmiş uygulamalarında Microsoft teknolojileri
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Bulut için iyileştirilmiş uygulamalarında Microsoft teknolojileri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 3c5886dc3583a5d4a6cc9566556edbe1822ad6d1
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315186"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Bulut için iyileştirilmiş uygulamalarında Microsoft teknolojileri

Aşağıdaki liste, Araçlar, teknolojileri ve bulut iyileştirilmiş uygulamaları için gereksinimleri olarak tanınır çözümleri açıklar. Bulut için iyileştirilmiş öğeleri önceliklerinizden bağlı olarak seçerek veya yavaş yavaş benimseyebilirsiniz.

-   **Bulut altyapısı**: işlem platformu, işletim sistemi, ağ ve depolama alanı sağlar altyapı. Microsoft Azure bu düzeyde konumlandırıldı.

-   **Çalışma zamanı**: Bu katmanda uygulamayı çalıştırmak için bir ortam sağlar. Kapsayıcıları kullanıyorsanız, bu katman, genellikle dayanır [Docker altyapısına](https://docs.docker.com/engine/)Linux ana bilgisayarlarda veya Windows konakları üzerinde çalışıyor. ([Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) ile Windows Server 2016'dan başlayarak desteklenmektedir. Windows kapsayıcılar olan en iyi seçenek Windows üzerinde çalışan var olan .NET Framework uygulamaları için.)

-   **Yönetilen bulut**: yönetilen bir bulut seçeneği seçtiğinizde, gider ve ağ yapılandırmasını yönetmek ve temel altyapı, sanal makineleri, işletim sistemi yamalarını destekleme karmaşıklığını önleyebilirsiniz. Iaas kullanarak geçirmek seçerseniz, ilişkili maliyetler ve bu görevlerin tümü için sorumlu. Yönetilen bir bulut seçenekte, yalnızca uygulamalar ve geliştirme hizmetler yönetin. Bulut hizmeti sağlayıcısı genellikle şey yönetir. Examples of managed cloud services in Azure include [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/), and managed compute services like [VM scale sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [Azure App Service](https://azure.microsoft.com/services/app-service/), and [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

-   **Uygulama geliştirme**: kapsayıcılarında çalışan uygulamaları derlerken çok sayıda dillerden seçebilirsiniz. Bu kılavuz odaklanır [.NET](https://www.microsoft.com/net), ancak/Java, Node.js, Python, yay gibi diğer diller kullanarak kapsayıcı tabanlı uygulamalar geliştirmek veya gidin.

-   **İzleme, günlüğe kaydetme ve denetim telemetri**: izleme ve denetim uygulamaları ve bulutta çalışan kapsayıcılar yeteneği her bulut için iyileştirilmiş uygulama için kritik öneme sahiptir. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) ve [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) bulut iyileştirilmiş uygulamaları için izleme ve denetim sağlayan ana Microsoft araçlardır.

-   **Sağlama**: Otomasyon araçları, altyapı sağlamak ve birden çok ortamlara (üretim, test, hazırlık) bir uygulama dağıtmanıza yardımcı. Bir uygulamanın yapılandırma ve ortamını yönetmek için Chef ve Puppet gibi araçlar kullanın. Bu katman, aynı zamanda daha basit ve daha doğrudan yaklaşımlar kullanılarak uygulanabilir. Örneğin, doğrudan Azure komut satırı araçları, arabirimi (Azure CLI) kullanarak dağıtın ve sonra sürekli dağıtım kullanın ve yönetim ardışık düzenlerinde yayın [Visual Studio Team Services](https://visualstudio.microsoft.com/team-services/).

-   **Uygulama yaşam döngüsü**: [Visual Studio Team Services](https://visualstudio.microsoft.com/team-services/) ve Jenkins gibi başka araçlar olan yardımcı yerleşik otomasyon sunucuları uygulamak CI/CD ardışık düzen, yayın yönetimi dahil olmak üzere.

Bu bölümde ve ilgili izlenecek yollar, sonraki bölümlerde özellikle çalışma zamanı katman (Windows kapsayıcıları) hakkındaki ayrıntıları odaklanır. Kılavuzu, Windows Server 2016 (ve sonraki sürümler) Windows kapsayıcılarında VM'ler ve Azure kapsayıcı örnekleri dağıtma yöntemleri açıklar. Ayrıca Azure uygulama hizmeti gibi daha gelişmiş PaaS platformlarda ve orchestrator Azure Service Fabric ve Azure Kubernetes hizmeti gibi ele alınmaktadır.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Tek yapılı uygulamaları *için* Bulutla optimize edilmiş olabilir

Tek yapılı uygulamaların (mikro üzerinde dayalı olmayan uygulamalar) vurgulamak önemlidir *yapabilirsiniz* bulut iyileştirilmiş uygulamalar. Yapı ve model kapsayıcıları, kesintisiz teslim ve DevOps bir bileşimini kullanarak bulut yararlanmak tek yapılı uygulamaları çalıştırmak. Varolan bir tek yapılı uygulama için iş hedeflerinize doğru ise, onu modernize ve kolaylaştırır Bulutla optimize edilmiş.

Benzer şekilde, tek yapılı uygulamaları bulut iyileştirilmiş uygulamaları olabiliyorsa, N katmanlı uygulamalar gibi diğer, daha karmaşık mimarileri bulut iyileştirilmiş uygulamaları olarak da modernized.

>[!div class="step-by-step"]
[Önceki](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
[sonraki](what-about-cloud-native-applications.md)
