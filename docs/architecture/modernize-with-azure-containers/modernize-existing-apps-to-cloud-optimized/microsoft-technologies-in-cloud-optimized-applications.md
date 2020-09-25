---
title: Bulut için Iyileştirilmiş uygulamalarda Microsoft teknolojileri
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulut için Iyileştirilmiş uygulamalarda Microsoft teknolojileri
ms.date: 04/28/2018
ms.openlocfilehash: b257497835638dd65c894998e95bd7e9d784b7bf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172020"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Bulut için iyileştirilmiş uygulamalarda Microsoft teknolojileri

Aşağıdaki listede, buluta Iyileştirilmiş uygulamalar için gereksinimler olarak tanınan araçlar, teknolojiler ve çözümler açıklanmaktadır. Önceliklerinize bağlı olarak, buluta Iyileştirilmiş öğeleri seçmeli veya yavaş şekilde benimseyebilirsiniz.

- **Bulut altyapısı**: işlem platformunu, işletim sistemini, ağı ve depolamayı sağlayan altyapı. Microsoft Azure bu düzeyde konumlandırıldı.

- **Çalışma zamanı**: Bu katman, uygulamanın çalıştırılacağı ortamı sağlar. Kapsayıcılar kullanıyorsanız bu katman genellikle Linux Konakları veya Windows konakları üzerinde çalışan [Docker altyapısını](https://docs.docker.com/engine/)temel alır. ([Windows kapsayıcıları](/virtualization/windowscontainers/about/) , windows Server 2016 ile başlayarak desteklenir. Windows kapsayıcıları, Windows üzerinde çalışan mevcut .NET Framework uygulamaları için en iyi seçenektir.)

- **Yönetilen bulut**: yönetilen bir bulut seçeneğini belirlediğinizde, temel altyapıyı, VM 'leri, işletim sistemi düzeltme eklerini ve ağ yapılandırmasını yönetme ve desteklemeye yönelik harcama ve karmaşıklıktan kaçınabilirsiniz. IaaS kullanarak geçirmeyi seçerseniz, tüm bu görevlerden ve ilişkili maliyetlerin sorumluluğundadır. Yönetilen bir bulut seçeneğinde, yalnızca geliştirmiş olduğunuz uygulamaları ve Hizmetleri yönetirsiniz. Bulut hizmeti sağlayıcısı genellikle diğer her şeyi yönetir. Azure 'da yönetilen bulut hizmetlerine örnek olarak Azure [SQL veritabanı](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure depolama](https://azure.microsoft.com/services/storage/), [MySQL için Azure](https://azure.microsoft.com/services/mysql/)veritabanı, [PostgreSQL için Azure veritabanı](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)ve [VM Ölçek Kümeleri](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure App Service](https://azure.microsoft.com/services/app-service/)ve [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/container-service/)gibi yönetilen işlem hizmetleri dahildir.

- **Uygulama geliştirme**: kapsayıcılar içinde çalışan uygulamalar oluştururken birçok dil arasından seçim yapabilirsiniz. Bu kılavuz [.net](https://dotnet.microsoft.com)'e odaklanır, ancak Node.js, Python, Spring/Java veya Go gibi diğer dilleri kullanarak kapsayıcı tabanlı uygulamalar geliştirebilirsiniz.

- **İzleme, telemetri, günlüğe kaydetme ve denetim**: bulutta çalışan uygulamaları ve kapsayıcıları izleme ve denetleme özelliği, buluta iyileştirilmiş tüm uygulamalar için kritik öneme sahiptir. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) ve [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) , buluta iyileştirilmiş uygulamalar için izleme ve denetim sağlayan ana Microsoft araçlardır.

- **Sağlama**: otomasyon araçları altyapıyı sağlamanıza ve bir uygulamayı birden çok ortama dağıtmanıza yardımcı olur (üretim, test, hazırlama). Bir uygulamanın yapılandırmasını ve ortamını yönetmek için Chef ve Pupevcil hayvan gibi araçları kullanabilirsiniz. Bu katman, daha basit ve daha doğrudan yaklaşımlar kullanılarak da uygulanabilir. Örneğin, Azure komut satırı arabirimi (Azure CLı) araçları 'nı kullanarak doğrudan dağıtabilir ve ardından [Azure DevOps Services](https://azure.microsoft.com/services/devops/)'de sürekli dağıtım ve sürüm yönetimi işlem hatlarını kullanabilirsiniz.

- **Uygulama yaşam döngüsü**: Jenkins gibi [Azure DevOps Services](https://azure.microsoft.com/services/devops/) ve diğer araçlar, sürüm yönetimi de dahil olmak üzere CI/CD işlem hatlarını uygulamanıza yardımcı olan bir yerleşik Otomasyon sunucularıdır.

Bu bölümün sonraki bölümleri ve ilgili izlenecek yollar, özellikle çalışma zamanı katmanı (Windows kapsayıcıları) hakkındaki ayrıntılara odaklanmaktadır. Bu kılavuzda Windows Server 2016 ' de (ve sonraki sürümlerde) Windows kapsayıcıları dağıtma yolları ve Azure Container Instances açıklanmaktadır. Ayrıca Azure Kubernetes hizmeti gibi Azure App Service ve Orchestrator gibi gelişmiş PaaS platformlarını da kapsamaktadır.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Tek *parçalı uygulamalar buluta* en iyi duruma getirilebilir

Tek parçalı uygulamaların (mikro hizmetleri temel alan *uygulamalar) bulutta* iyileştirilmiş uygulamalar olduğunu vurgulamak önemlidir. Kapsayıcılar, sürekli teslim ve DevOps birleşimini kullanarak bulut bilgi işlem modelinden faydalanan tek parçalı uygulamalar oluşturup çalıştırabilirsiniz. Mevcut bir tek parçalı uygulama, iş amaçlarınız için uygun ise, modernleştirin ve buluta Iyileştirmeyi sağlayabilirsiniz.

Benzer şekilde, tek parçalı uygulamalar bulut için Iyileştirilmiş uygulamalar ise, N katmanlı uygulamalar gibi diğer karmaşık mimarilerin de bulut için Iyileştirilmiş uygulamalar olarak da yapılandırılabilir.

>[!div class="step-by-step"]
>[Önceki](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md) 
> [Sonraki](what-about-cloud-native-applications.md)
