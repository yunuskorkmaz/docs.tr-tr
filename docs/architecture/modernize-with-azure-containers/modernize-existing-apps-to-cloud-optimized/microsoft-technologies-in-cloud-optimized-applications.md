---
title: Bulut Için Optimize Edilmiş uygulamalarda Microsoft teknolojileri
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Bulut Için Optimize Edilmiş uygulamalarda Microsoft teknolojileri
ms.date: 04/28/2018
ms.openlocfilehash: c5222ba13258f9c8a40ca3b9ce240aeb9f41da63
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546516"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Bulut için optimize edilmiş uygulamalarda Microsoft teknolojileri

Aşağıdaki listede, Bulut Için Optimize Edilmiş uygulamalar için gereksinim olarak kabul edilen araçlar, teknolojiler ve çözümler açıklanmaktadır. Önceliklerinize bağlı olarak Bulut Tarafından Optimize Edilmiş öğeleri seçici veya aşamalı olarak benimseyebilirsiniz.

- **Bulut altyapısı**: İşlem platformu, işletim sistemi, ağ ve depolama sağlayan altyapıdır. Microsoft Azure bu düzeyde konumlandırılmıştır.

- **Çalışma Süresi**: Bu katman, uygulamanın çalışması için ortam sağlar. Kapsayıcılar kullanıyorsanız, bu katman genellikle [Docker Engine'e](https://docs.docker.com/engine/)dayanır ve Linux ana bilgisayarlarında veya Windows ana bilgisayarlarında çalışır. ([Windows Kapsayıcıları,](https://docs.microsoft.com/virtualization/windowscontainers/about/) Windows Server 2016 ile birlikte desteklenir. Windows Kapsayıcıları, Windows'da çalışan varolan .NET Framework uygulamaları için en iyi seçimdir.)

- **Yönetilen bulut**: Yönetilen bir bulut seçeneğini seçtiğinizde, temel altyapıyı, VM'leri, işletim sistemi yamaları ve ağ yapılandırmasını yönetme ve destekleme giderini ve karmaşıklığını önleyebilirsiniz. IaaS kullanarak geçiş yapmayı seçerseniz, tüm bu görevlerden ve ilişkili maliyetlerden siz sorumlusunuz. Yönetilen bir bulut seçeneğinde, yalnızca geliştirdiğiniz uygulamaları ve hizmetleri yönetirsiniz. Bulut hizmeti sağlayıcısı genellikle diğer her şeyi yönetir. Azure'daki yönetilen bulut hizmetlerine örnek olarak [Azure SQL Veritabanı, Azure](https://azure.microsoft.com/services/sql-database) [Redis Önbelleği,](https://azure.microsoft.com/services/cache/) [Azure Cosmos DB, Azure](https://azure.microsoft.com/services/cosmos-db/) [Depolama,](https://azure.microsoft.com/services/storage/) [MySQL için Azure Veritabanı,](https://azure.microsoft.com/services/mysql/) [PostgreSQL için Azure Veritabanı,](https://azure.microsoft.com/services/postgresql/) [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)ve [VM ölçek setleri,](https://azure.microsoft.com/services/virtual-machine-scale-sets/) [Azure Uygulama Hizmeti](https://azure.microsoft.com/services/app-service/)ve Azure [Kubernetes Hizmeti](https://azure.microsoft.com/services/container-service/)gibi yönetilen işlem hizmetleri verilebilir.

- **Uygulama geliştirme**: Kapsayıcılarda çalışan uygulamalar oluştururken birçok dil arasından seçim yapabilirsiniz. Bu kılavuz [.NET'e](https://dotnet.microsoft.com)odaklanır, ancak Node.js, Python, Spring/Java veya Go gibi diğer dilleri kullanarak kapsayıcı tabanlı uygulamalar geliştirebilirsiniz.

- **İzleme, telemetri, günlüğe kaydetme ve denetleme**: Bulutta çalışan uygulamaları ve kapsayıcıları izleme ve denetleme becerisi Bulut Tarafından Optimize Edilmiş tüm uygulamalar için çok önemlidir. [Azure Uygulama Öngörüleri](https://azure.microsoft.com/services/application-insights/) ve [Microsoft Operations Management Suite,](https://www.microsoft.com/cloud-platform/operations-management-suite) Bulut Tarafından Optimize Edilmiş uygulamaların izlenmesini ve denetlenmesisağlayan başlıca Microsoft araçlarıdır.

- **Sağlama**: Otomasyon araçları, altyapıyı sağlamanıza ve bir uygulamayı birden çok ortama (üretim, test, evreleme) dağıtmanıza yardımcı olur. Bir uygulamanın yapılandırmasını ve ortamını yönetmek için Chef ve Puppet gibi araçları kullanabilirsiniz. Bu katman daha basit ve daha doğrudan yaklaşımlar kullanılarak da uygulanabilir. Örneğin, Azure komut satırı arabirimi (Azure CLI) aracını kullanarak doğrudan dağıtabilir ve ardından [Azure DevOps Hizmetleri'nde](https://azure.microsoft.com/services/devops/)sürekli dağıtım ve sürüm yönetimi ardışık hatlarını kullanabilirsiniz.

- **Uygulama yaşam döngüsü**: [Azure DevOps Hizmetleri](https://azure.microsoft.com/services/devops/) ve Jenkins gibi diğer araçlar, sürüm yönetimi de dahil olmak üzere CI/CD ardışık hatlarını uygulamanıza yardımcı olan otomasyon sunucuları dır.

Bu bölümün sonraki bölümleri ve ilgili izthroughs, özellikle çalışma zamanı katmanı (Windows Kapsayıcıları) hakkında ayrıntılara odaklanır. Kılavuz, Windows Kapsayıcılarını Windows Server 2016 'da (ve daha sonraki sürümlerde) VM'lerde ve Azure Kapsayıcı Örnekleri'nde dağıtma yollarını açıklar. Ayrıca Azure Uygulama Hizmeti ve Azure Kubernetes Service gibi orkestratör gibi daha gelişmiş PaaS platformlarını da kapsar.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Monolitik *uygulamalar* Bulut Tarafından Optimize Edilebilir

Yekpare uygulamaların (mikro hizmetlere dayanmayan uygulamalar) Bulut Tarafından Optimize Edilmiş uygulamalar *olabileceğini* vurgulamak önemlidir. Kapsayıcılar, sürekli teslimat ve DevOps'lerin bir birleşimini kullanarak bulut bilgi işlem modelinden yararlanan yekpare uygulamalar oluşturabilir ve çalıştırabilirsiniz. Mevcut yekpare bir uygulama iş hedefleriniz için uygunsa, onu modernize edebilir ve Bulut Tarafından Optimize Edilebilebilir hale getirebilirsiniz.

Benzer şekilde, yekpare uygulamalar Bulut için Optimize Edilmiş uygulamalar alabiliyorsa, N-Tier uygulamaları gibi diğer, daha karmaşık mimariler de Bulut Için Optimize Edilmiş uygulamalar olarak modernize edilebilir.

>[!div class="step-by-step"]
>[Önceki](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[Sonraki](what-about-cloud-native-applications.md)
