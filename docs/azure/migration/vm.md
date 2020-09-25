---
title: Bir ASP.NET Web uygulamasını bir Azure VM 'ye geçirme
description: Şirket içinden bir ASP.NET Web uygulamasını bir Azure sanal makinesine geçirmeyi öğrenin.
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 940243310c5e6ed13d2a42c8d9d87244200479f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171565"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Bir ASP.NET Web uygulamasını bir Azure sanal makinesine geçirme

Bu belgede, ASP.NET Web uygulamalarının Şirket içinden bir Azure sanal makinesine nasıl geçirileceğiyle ilgili bir genel bakış sunulmaktadır.

## <a name="quickstart"></a>Hızlı Başlangıç

Bir sanal makine oluşturmayı ve uygulamanızı nasıl yayımlayacağınızı öğrenin: [bir Azure VM 'ye yayımlama](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>Başlarken

Bu öğreticiler, bir sanal makine oluşturma (veya geçirme), Web uygulamanızı bu uygulamada yayımlama ve Azure 'da uygulamanızı desteklemek için gerekebilecek diğer görevleri gösterir.

- Aşağıdaki seçeneklerden birini kullanarak Azure 'da ASP.NET uygulamanız için bir sanal makine oluşturun:
  - [ASP.NET uygulamaları için yeni bir sanal makine oluşturma](https://go.microsoft.com/fwlink/?linkid=863237)
  - [Mevcut bir şirket içi VMWare sanal makinesini geçirme](/azure/migrate/tutorial-migrate-vmware)
  - [Mevcut bir şirket içi Hyper-V sanal makinesini geçirme](/azure/migrate/tutorial-migrate-hyper-v)
- [Visual Studio 'Yu kullanarak uygulamanızı yayımlayın](https://go.microsoft.com/fwlink/?linkid=863240)
- [VM 'niz için güvenli bir sanal ağ oluşturma](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [Uygulamanız için bir CI/CD işlem hattı oluşturun](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [Yüksek kullanılabilirlik ve ölçeklenebilirlik için bir VM Ölçek kümesine taşıma](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>Dikkat edilmesi gerekenler

### <a name="benefits"></a>Yararları

Sanal makineler, bir uygulamayı Şirket içinden buluta geçirmek için en kolay yolu sunar. Kendi veri merkezlerinizi koruma gereksinimini ortadan kaldırarak, uygulamanızın şirket içinde kullandığı ortamı çoğaltmanıza olanak sağlar. Sanal Makine Ölçek Kümeleri, sanal makinelerde çalışan uygulamalar için yüksek kullanılabilirlik ve ölçeklenebilirlik sağlar.

### <a name="virtual-machine-size"></a>Sanal makine boyutu

İş yükünüz için en iyi duruma getirilmiş sanal makine boyutunu ve türünü seçin. Daha fazla bilgi için bkz. [Azure 'Da Windows sanal makineleri Için boyutlar](/azure/virtual-machines/windows/sizes).

### <a name="maintenance"></a>Bakım

Tıpkı şirket içi bir makine gibi, sanal makine<sup>&#42;</sup>bakım ve güncelleştirme sorumluluğunuz de sorumludur. Uygulamanız, [Azure App Service](/azure/app-service/) veya bir [kapsayıcıda](/azure/app-service/containers/)bir hizmet olarak platform (PaaS) ortamında (Bu gereksinimi ortadan kaldıracak) çalıştırılabilir.

*<sup> </sup> [Sanal makine ölçek kümeleri için otomatik işletim sistemi yükseltmeleri](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)&#42;Şu anda bir önizleme hizmeti olarak sunulmaktadır.*

### <a name="virtual-networks"></a>Sanal Ağlar

Azure sanal ağları şunları sağlar:

- Denetlediğiniz bir karma altyapı oluşturun
- Kendi IP adreslerinizi ve DNS sunucularınızı getirin
- Uygulamalarınız için yalıtılmış ve yüksek oranda güvenli bir ortam oluşturun
- Çeşitli [bağlantı seçeneklerinden](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) bırını kullanarak Sanal ağınızı şirket içi ağınıza bağlayın
- [ExpressRoute](https://azure.microsoft.com/services/expressroute/) kullanarak sanal makinenizi şirket içi ağınızla tümleştirin

Başlamak için bkz. [sanal ağ belgeleri](/azure/virtual-network/)

### <a name="active-directory"></a>Active Directory

Birçok uygulama kimlik doğrulama ve kimlik yönetimi için Active Directory kullanır.

- Azure AD Connect, şirket içi dizinlerinizi Azure Active Directory tümleştirmenizi sağlar. Başlamak için bkz. Şirket [içi dizinlerinizi Azure Active Directory tümleştirme](/azure/active-directory/connect/active-directory-aadconnect).
- Alternatif olarak, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) , uygulamanızın şirket içi Active Directory erişmesini sağlar.

### <a name="sql-databases"></a>SQL Veritabanları

Uygulamanız şirket içi bir veritabanı kullanıyorsa, uygulamanız varsayılan olarak bu uygulamayla iletişim kuramayacak. Şunlardan birini yapabilirsiniz:

- Uygulamanızın şirket içinde çalışan veritabanınıza erişmesini sağlayan bir karma ağ yapılandırın.
- Veritabanınızı Azure 'a geçirin. Daha fazla bilgi için bkz. [SQL Server veritabanınızı Azure 'A geçirme](sql.md).

### <a name="high-availability-and-scalability"></a>Yüksek kullanılabilirlik ve ölçeklenebilirlik

#### <a name="virtual-machine-scale-sets"></a>Sanal Makine Ölçek Kümeleri

Uygulamanızın kullanılabilirliği ve ölçeklenebilirliğini artırmak için uygulamanızın yüksek oranda kullanılabilir olduğundan ve ölçekleyebilir olduğundan emin olmak istiyorsunuz, VM görüntünüzü bir Azure sanal makine ölçek kümesine geçirin. VM Ölçek Kümeleri, önceden yapılandırdığınız mevcut bir VM 'yi kullanma veya uygulamanızla bir görüntü oluşturmak için derleme işlem hattı ayarlama olanağı sağlar.

Başlamak için bkz. [sanal makine ölçek kümelerinde uygulamanızı dağıtma](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

#### <a name="centralized-logging"></a>Merkezi günlük kaydı

Uygulamanızı birden çok örnek genelinde çalıştırırken günlüklerinizi [Azure depolama](/azure/storage/)gibi merkezi bir konumda depolamayı düşünün.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Azure’a SQL Server veritabanını geçirme](sql.md)
