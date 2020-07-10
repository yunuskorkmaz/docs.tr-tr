---
title: Doğru Azure barındırma seçeneğini belirleyin
description: ASP.NET Web uygulamanız için hangi Azure geçiş yolunun doğru olduğunu öğrenin.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: 162dc8eb87dfd78d050b93b1c24ac573d7092126
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174302"
---
# <a name="choose-the-right-azure-hosting-option"></a>Doğru Azure barındırma seçeneğini belirleyin

Bu makalede, mevcut .NET Framework uygulamalarınızı Şirket içinden Azure 'a geçirirken Azure 'da sahip olduğunuz birden çok seçenek arasındaki önemli noktalar ve karşılaştırmalar sağlanmıştır.

Mevcut .NET uygulamalarını Azure 'a geçirirken göz önünde bulundurmanız gereken temel bölgeler şunlardır:

1. İşlem seçenekleri
1. Veritabanı seçenekleri
1. Ağ ve güvenlik konuları
1. Kimlik doğrulama ve yetkilendirme konuları

## <a name="compute-choices"></a>İşlem seçenekleri

Mevcut .NET Framework uygulamaları Azure 'a geçirirken birden çok seçeneğiniz vardır. Ancak .NET Framework Windows 'a bağlı olduğundan, aşağıdaki seçimler Windows tabanlı işlem hizmetleri ile sınırlıdır.

Aşağıdaki tabloda, mevcut .NET uygulamanız için doğru işlem geçiş yolunu seçmenize yardımcı olacak çeşitli karşılaştırmalar ve öneriler gösterilmektedir.

|                 | Azure VM’leri | Azure App Service | Windows Kapsayıcıları |
|-----------------|-----------|-------------------|--------------------|
|Kullanılması gereken durumlar      |<ul><li>Uygulamanın, sunucuda ve yerel. msi yüklemelerinde güçlü bağımlılıkları vardır.</li><li>En kolay uygulama geçiş yolunu istiyorsunuz</li></ul>|Uygulamanın sunucuda bağımlılığı yok, bir veritabanı sunucusuna erişen yalnızca temiz bir ASP.NET Web uygulaması (MVC, WebForm) veya N katmanlı uygulama (Web API 'SI, WCf). |<ul><li>Uygulamanın özgün sunucuda bağımlılıkları vardır ancak bu bağımlılıklar Docker Windows görüntüsüne dahil edilebilir.</li><li>Uygulamayı [bulut DevOps-Ready](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md) olacak şekilde modernleştirin etmek ister misiniz?</li></ul>|
|Profesyonelleri & avantajları  |<ul><li>En kolay geçiş yolu</li><li>Tanıdık ortam. Dağıtım ortamı bir VM olduğundan, şirket içi sunuculara benzer.</li></ul> |Sürekli PaaS bakımı, Azure 'da uygulamaları yönetmenin ve ölçeklendirmenin en kolay yolu. |<ul><li>Daha sonra Cloud DevOps-uygulamanın kapsayıcılarına dahil edilen bağımlılıklarla hazır.</li><li>Neredeyse .NET/C # kodunu yeniden düzenleme gerekmez.</li></ul> |
|Dezavantajlar             |IaaS 'dir. Bakım maliyetlidir. Ağ iletişimi, yük dengeleyici, genişleme, IIS yönetimi vb. gibi VM 'nin altyapısını yönetmeniz gerekir. |<ul><li>Tüm uygulamalar [desteklenmez](https://appmigration.microsoft.com/assessment)</li><li>Bazı uygulamaların yeniden düzenlenmiş ve hatta biraz daha yüksek bir şekilde kullanılabilmesi için Azure App Service desteklemesi gerekebilir.</li></ul> |<ul><li>Docker 'ın becerileri öğrenme eğrisi</li><li>Bazı kod ve uygulama yapılandırma ayarları değişir</li></ul>|
|Gereksinimler |Şirket içi için uygulamadan aynı gereksinimlere sahip Windows Server VM | [Hazırlık denetimlerinde](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks)Azure App Service gereksinimler belirtildi. |<ul><li>[Docker altyapısı-Windows Server 2019 için kuruluş](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />veya</li><li>[Azure Container Service (AKS)](https://azure.microsoft.com/services/container-service/) (Kubernetes Orchestrator)<br />veya<li>[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) Orchestrator</li></ul> |
|Geçiş yapma |Bkz. [Azure sanal makinelerine geçirme](vm.md) | Bkz. [geçirme Azure App Service](app-service.md) | [Azure ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirmede](https://aka.ms/liftandshiftwithcontainersebook) açıklanan konuları, senaryoları ve izlenecek yolları izleyin. |

Aşağıdaki akış çizelgesi diyagramı, mevcut .NET Framework uygulamalarınız için Azure 'a geçiş planlarken bir karar ağacı gösterir. Mümkünse, ilk olarak seçeneğini deneyin, ancak seçenek B, gerçekleştirilecek en kolay yoldur.

![Barındırma kararı ağacını gösteren akış çizelgesi](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Veritabanı seçenekleri

İlişkisel veritabanlarını Azure 'a geçirirken birden çok seçeneğiniz vardır. Mevcut .NET uygulamanız için doğru veritabanı geçiş yolunu seçmenize yardımcı olmak üzere [SQL Server veritabanınızı Azure 'A geçirme](sql.md) konusuna bakın.

## <a name="networking-and-security-considerations"></a>Ağ ve güvenlik konuları

Uygulamalar Microsoft Azure gibi bir genel buluta dağıtıldığında, [Azure ile şirket içi arasında bir DMZ](/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) veya [Azure ile Internet arasında bir DMZ](/azure/architecture/reference-architectures/dmz/secure-vnet-dmz)gibi [ağ DMZs oluşturarak](/azure/architecture/reference-architectures/dmz/)belirli ağları yalıtmak ve güvenli hale getirmek isteyebilirsiniz. DMZs, [Azure sanal ağı](/azure/virtual-network/virtual-networks-overview)ile uygulanabilir.

Azure sanal ağları şunları sağlar:

- Denetlediğiniz bir karma altyapı oluşturun
- Kendi IP adreslerinizi ve DNS sunucularınızı getirin
- IPSec VPN veya ExpressRoute ile bağlantılarınızın güvenliğini sağlama
- Alt ağlar arasındaki trafik üzerinde ayrıntılı denetim sağlayın
- Sanal gereçler ile gelişmiş ağ topolojileri oluşturma
- Uygulamalarınız için yalıtılmış ve yüksek oranda güvenli bir ortam alın

Kendi sanal ağınızı oluşturmaya başlamak için bkz. [Azure sanal ağ belgeleri](/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Azure 'a geçiş yaparken kimlik doğrulama ve yetkilendirme konuları

Buluta taşınan herhangi bir kuruluşun önemli bir sorunu güvenlik. Çoğu şirket, bir güvenlik modeli tasarlamak ve geliştirmek için önemli miktarda zaman, para ve mühendislik kazanmıştır ve kimlik depoları ve çoklu oturum açma çözümleri gibi mevcut yatırımlardan faydalanabilir.

Şirket içinde çalışan birçok mevcut Enterprise B2E .NET uygulaması, kimlik doğrulama ve kimlik yönetimi için Active Directory kullanır. Azure AD Connect, şirket içi dizinlerinizi Azure Active Directory tümleştirmenizi sağlar. Başlamak için bkz. Şirket [içi dizinlerinizi Azure Active Directory tümleştirme](/azure/active-directory/connect/active-directory-aadconnect).

Azure Active Directory ilgili daha fazla planlama için [karma kimlik çözümünüz Için kimlik gereksinimleri](/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) bölümüne bakın.

Diğer kimlik doğrulama protokolü seçimleri, tüketiciye yönelik uygulamalarda ortak olan [OAuth](https://en.wikipedia.org/wiki/OAuth) ve [OpenID](https://en.wikipedia.org/wiki/OpenID)' dir. Identityserver4 tarafından OAuth kullanılarak Sarmalanan ASP.NET Identity SQL veritabanı gibi otonom kimlik veritabanlarını kullanırken, genellikle şirket içi veritabanlarına veya dizinlere bağlantı gerekmez.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Bir ASP.NET Web uygulamasını Azure App Service geçirme](app-service.md)
