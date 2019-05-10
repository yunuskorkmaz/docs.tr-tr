---
title: Bulut için iyileştirilmiş uygulamalarda Microsoft teknolojileri
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Bulut için iyileştirilmiş uygulamalarda Microsoft teknolojileri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 21ba318c3a59175dadde86ff247c6e41e7f85c0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627276"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Bulut için iyileştirilmiş uygulamalarda Microsoft teknolojileri

Aşağıdaki listede, araçları, teknolojileri ve bulut için iyileştirilmiş uygulamalar için gereksinimleri tanınan çözümleri açıklanmaktadır. Bulut için iyileştirilmiş öğeleri bağlı olarak, önceliklerinizden seçmeli veya yavaş yavaş benimseyebilirsiniz.

- **Bulut altyapısı**: Bilgi işlem platformu, işletim sistemi, ağ ve depolama sağlayan altyapı. Microsoft Azure, bu düzeyde konumlandırıldı.

- **Çalışma zamanı**: Bu katman, uygulamayı çalıştırmak için ortamı sağlar. Kapsayıcıları kullanıyorsanız, bu katmanda genellikle dayanır [Docker altyapısı](https://docs.docker.com/engine/), Linux ana bilgisayarları veya Windows ana bilgisayarlarda çalışır. ([Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) ile Windows Server 2016'den itibaren desteklenir. Windows kapsayıcıları olan Windows üzerinde var olan .NET Framework uygulamaları için en iyi seçenek.)

- **Yönetilen bulut**: Yönetilen bir bulut seçeneğini belirttiğinizde maliyetinden ve karmaşasından yönetme ve destekleme temel alınan altyapı, VM'ler, işletim sistemi düzeltme ekleri ve ağ yapılandırmasını önleyebilirsiniz. Iaas kullanılarak geçirmeye seçerseniz, ilişkili maliyetleri ve bu görevlerin tümü için sorumlu olursunuz. Yönetilen bir bulut seçeneğinde, yalnızca uygulama ve geliştirme Hizmetleri yönetin. Bulut hizmeti sağlayıcısı, genellikle diğer her şey yönetir. Azure'da yönetilen bulut Hizmetleri örnekleri [Azure SQL veritabanı](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure depolama](https://azure.microsoft.com/services/storage/), [MySQL için azure veritabanı](https://azure.microsoft.com/services/mysql/), [PostgreSQL için Azure veritabanı](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)ve yönetilen gibi işlem hizmetlerini [VM ölçek Ayarlar](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [Azure App Service](https://azure.microsoft.com/services/app-service/), ve [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/container-service/).

- **Uygulama geliştirme**: Kapsayıcılarda çalıştırılan uygulamalar oluştururken, birçok dillerden seçebilirsiniz. Bu kılavuzda odaklanır [.NET](https://www.microsoft.com/net), ancak/Java, Node.js, Python, Spring gibi diğer dilleri kullanarak kapsayıcı tabanlı uygulamalar geliştirebilir veya gidin.

- **İzleme, günlüğe kaydetme ve denetim telemetri**: Uygulamaları izleyin ve denetleyin ve bulutta çalışan kapsayıcılar için herhangi bir bulut için iyileştirilmiş uygulama için kritik önem taşır. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) ve [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) bulut için iyileştirilmiş uygulamalar için izleme ve denetim sağlamak ana Microsoft araçlardır.

- **Sağlama**: Otomasyon araçları altyapıyı sağlamak ve bir uygulama birden çok ortama (üretim, test, hazırlık) dağıtmanıza yardımcı olur. Chef ve Puppet gibi araçlar, uygulamanın yapılandırma ve ortamı yönetmek için kullanabilirsiniz. Bu katman, daha kolay ve doğrudan yaklaşımları kullanarak da uygulanabilir. Örneğin, Azure komut satırı araçları, arabirimi (Azure CLI) kullanarak doğrudan dağıtabilir ve ardından sürekli dağıtımı kullanın ve release management işlem hatlarında [Azure DevOps Hizmetleri](https://azure.microsoft.com/services/devops/).

- **Uygulama yaşam döngüsü**: [Azure DevOps hizmetleriyle](https://azure.microsoft.com/services/devops/) ve Jenkins gibi başka araçlar olan yardımcı olan yerleşik otomasyon sunucuları uygulamak CI/CD işlem hatları, sürüm yönetimi dahil olmak üzere.

Bu bölümde ve ilgili izlenecek yollar, sonraki bölümlerde özel çalışma zamanı katman (Windows kapsayıcıları) hakkındaki ayrıntıları odaklanır. Yönergeler, Windows Server 2016 (ve sonraki sürümler) Windows kapsayıcıları VM'ler ve Azure Container Instances'a dağıtma yöntemleri açıklar. Ayrıca, Azure App Service gibi daha gelişmiş PaaS platformları ve Azure Service Fabric ve Azure Kubernetes hizmeti gibi orchestrator kapsar.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Tek yapılı uygulamaları *olabilir* Bulutla optimize edilmiş olabilir

Bu tek parçalı uygulamalarla (üzerinde mikro hizmet tabanlı olmayan uygulamalar) vurgulamak önemlidir *olabilir* bulut için iyileştirilmiş uygulamalar. Yapı ve model kapsayıcılar, sürekli teslim ve Devops'a genel bir bileşimini kullanarak bulut avantajlarından yararlanmak tek parçalı uygulamalarla çalışır. Mevcut tek parça bir uygulamayı iş hedeflerinizi doğru ise, bunu modernleştirin ve hale Bulutla optimize edilmiş.

Benzer şekilde, tek yapılı uygulamaları bulut için iyileştirilmiş uygulamalar olabilir, N katmanlı uygulamalar gibi diğer, daha karmaşık mimarileri bulut için iyileştirilmiş uygulamalar olarak da modernleştirdiğini.

>[!div class="step-by-step"]
>[Önceki](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[İleri](what-about-cloud-native-applications.md)