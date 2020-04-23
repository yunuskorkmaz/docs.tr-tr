---
title: Doğru Azure barındırma seçeneğini seçin
description: ASP.NET web uygulamanız için hangi Azure geçiş yolunun doğru olduğunu öğrenin.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: a8ad946b03f97272cb8685620858af6b21a372dc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "82072111"
---
# <a name="choose-the-right-azure-hosting-option"></a>Doğru Azure barındırma seçeneğini seçin

Bu makalede, varolan .NET Framework uygulamalarınızı şirket içinde Azure'a geçirdiğinizde Azure'da sahip olduğunuz birden çok seçenek arasında dikkate alınması gereken hususlar ve karşılaştırmalar sağlanmaktadır.

Varolan .NET uygulamalarını Azure'a geçirerken göz önünde bulundurulması gereken temel alanlar şunlardır:

1. İşlem seçenekleri
1. Veritabanı seçenekleri
1. Ağ ve güvenlik konuları
1. Kimlik doğrulama ve yetkilendirme konuları

## <a name="compute-choices"></a>İşlem seçenekleri

Varolan .NET Framework uygulamalarını Azure'a geçirdiğinizde birden çok seçeneğiniz vardır. Ancak,.NET Framework Windows'a bağlı olduğundan, aşağıdaki seçenekler Windows tabanlı işlem hizmetleriyle sınırlıdır.

Aşağıdaki tablo, varolan .NET uygulamanız için doğru bilgi işlem geçiş yolunu seçmenize yardımcı olacak çeşitli karşılaştırmalar ve öneriler gösterir.

|                 | Azure VM’leri | Azure App Service | Windows Kapsayıcıları |
|-----------------|-----------|-------------------|--------------------|
|Kullanılması gereken durumlar      |<ul><li>Uygulama sunucu ve yerel .msi yüklemeleri üzerinde güçlü bağımlılıkları vardır.</li><li>En kolay uygulama geçiş yolunu istiyorsunuz</li></ul>|Uygulama sunucu üzerinde hiçbir bağımlılığı vardır, sadece temiz bir ASP.NET web uygulaması (MVC, WebForm) veya N-Tier uygulaması (Web API, WCf) bir veritabanı sunucusuna erişen. |<ul><li>Uygulamanın özgün sunucuya bağımlılıkları vardır, ancak bu bağımlılıklar Docker Windows görüntüsüne eklenebilir.</li><li>[Uygulamayı Cloud DevOps-Ready](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md) olacak şekilde modernize etmek istiyorum</li></ul>|
|Artıları & faydaları  |<ul><li>En kolay geçiş yolu</li><li>Tanıdık bir ortam. Dağıtım ortamı bir VM'dir, bu nedenle şirket içi sunuculara benzer.</li></ul> |Azure'daki uygulamaları yönetmenin ve ölçeklendirmenin en basit yolu olan, devam eden PaaS bakımı. |<ul><li>Geleceğe hazırlanan Cloud DevOps-Ready bağımlılıkları uygulamanın kaplarına dahil edilmiştir.</li><li>.NET /C# kodunu yeniden düzenlemenize gerek yok.</li></ul> |
|Simgeler             |Bu IaaS. Bakım pahalıya mal olur. Ağ, yük dengeleyici, ölçeklendirme, IIS yönetimi ve benzeri konularda VM'nin altyapısını yönetmeniz gerekir. |<ul><li>Tüm uygulamalar [desteklenmez](https://appmigration.microsoft.com/assessment)</li><li>Bazı uygulamaların yeniden düzenlemesi ve hatta biraz yeniden tasarlanması gerekebilir, bu nedenle Azure Uygulama Hizmeti'ni desteklerler.</li></ul> |<ul><li>Docker'ın beceri öğrenme eğrisi</li><li>Bazı kod ve uygulama yapılandırma ayarları değişir</li></ul>|
|Gereksinimler |Windows Server VM, şirket içi uygulamayla aynı gereksinimlere sahip | [Hazır olma denetimlerinde](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks)belirtilen Azure Uygulama Hizmeti gereksinimleri. |<ul><li>[Docker Engine - Windows Server için Kurumsal 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />or</li><li>[Azure Konteyner Hizmeti (AKS)](https://azure.microsoft.com/services/container-service/) (Yani Kubernetes orkestratör)<br />or<li>[Azure Servis Kumaşı](https://azure.microsoft.com/services/service-fabric/) orkestratör</li></ul> |
|Geçiş yapma |Bkz. [Azure Sanal Makinelere Geçiş](vm.md) | Bkz. [Azure Uygulama Hizmetini Geçir](app-service.md) | Azure ve [Windows Kapsayıcıları e-Kitap ile mevcut .NET uygulamalarını modernize etmede](https://aka.ms/liftandshiftwithcontainersebook) açıklanan hususları, senaryoları ve walkthroughs'u izleyin |

Aşağıdaki akış şeması diyagramı, varolan .NET Framework uygulamalarınız için Azure'a geçiş planlarken bir karar ağacını gösterir. Uygunsa, önce A seçeneğini deneyin, ancak B seçeneği gerçekleştirmenin en kolay yoludur.

![Barındırma karar ağacını gösteren akış şeması](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Veritabanı seçenekleri

İlişkisel veritabanlarını Azure'a geçirerken birden çok seçeneğiniz vardır. Bkz. SQL [Server veritabanınızı Azure'a geçirip](sql.md) varolan .NET uygulamanız için doğru veritabanı geçiş yolunu seçmenize yardımcı olun.

## <a name="networking-and-security-considerations"></a>Ağ ve güvenlik konuları

Uygulamaları Microsoft Azure gibi genel bir buluta dağıtırken, Azure ile şirket içi arasında Bir [DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) veya Azure ile Internet arasında bir DMZ gibi ağ [DMZ'leri oluşturarak](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/)belirli ağları yalıtmak ve güvenli hale getirmek [isteyebilirsiniz.](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz) DMZ'ler [Azure Sanal Ağı](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)ile uygulanabilir.

Azure Sanal ağlar şunları yapmanızı sağlar:

- Kontrol ettiğiniz karma bir altyapı oluşturun
- Kendi IP adreslerinizi ve DNS sunucularınızı getirin
- Bir IPsec VPN veya ExpressRoute ile bağlantılarınızı emniyete ala
- Alt ağlar arasındaki trafik üzerinde parçalı denetim edin
- Sanal cihazlar kullanarak gelişmiş ağ topolojileri oluşturun
- Uygulamalarınız için izole ve son derece güvenli bir ortam elde edin

Kendi sanal ağınızı oluşturmaya başlamak için [Azure Sanal Ağ belgelerine](https://docs.microsoft.com/azure/virtual-network/)bakın.

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Azure'a geçiş yaparken kimlik doğrulama ve yetkilendirme hususları

Buluta taşınan herhangi bir kuruluşun en önemli endişesi güvenliktir. Çoğu şirket, bir güvenlik modeli tasarlamak ve geliştirmek için önemli miktarda zaman, para ve mühendislik yatırımı yapmış ve kimlik mağazaları ve tek oturum açma çözümleri gibi mevcut yatırımlardan yararlanabilmeleri önemlidir.

Şirket içinde çalışan birçok mevcut kuruluş B2E .NET uygulaması, kimlik doğrulama ve kimlik yönetimi için Active Directory kullanır. Azure AD Connect, şirket içi dizinlerinizi Azure Etkin Dizini ile tümleştirmenize olanak tanır. Başlamak için bkz. [Şirket içi dizinlerinizi Azure Etkin Dizini ile tümleştirin.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

Azure Active Directory ile ilgili daha fazla planlama için [karma kimlik çözümünüz için Kimlik gereksinimlerine](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) bakın.

Diğer kimlik doğrulama protokolü seçenekleri, tüketiciye yönelik uygulamalarda yaygın olan [OAuth](https://en.wikipedia.org/wiki/OAuth) ve [OpenID'dir.](https://en.wikipedia.org/wiki/OpenID) OAuth kullanarak IdentityServer4 tarafından sarılmış ASP.NET Kimlik SQL veritabanı gibi özerk kimlik veritabanları nı kullanırken, genellikle şirket içi veritabanlarına veya dizinlere bağlantı gerekmez.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [ASP.NET bir web uygulamasını Azure Uygulama Hizmetine geçirin](app-service.md)
