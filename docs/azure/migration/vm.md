---
title: bir ASP.NET Web uygulamasını Azure VM'ye geçirme
description: Bir ASP.NET Web uygulamasını şirket içinden Azure Sanal Makinesi'ne nasıl geçirteceklerini öğrenin.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072125"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>bir ASP.NET Web uygulamasını Azure Sanal Makinesine geçirme

Bu belge, ASP.NET bir web uygulamasını şirket içinde bir Azure Sanal Makinesine nasıl geçirilene ilişkin genel bir bakış sağlar.

## <a name="quickstart"></a>Hızlı Başlangıç

Sanal bir makine oluşturma yı ve uygulamanızı nasıl yayınlayacağınızı öğrenin: [Azure VM'de yayımlayın](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>Başlarken

Bu öğreticiler, sanal bir makine oluşturma (veya geçirme) adımlarını, web uygulamanızı bu makinede yayımlama adımlarını ve Azure'da uygulamanızı desteklemek için gerekli olabilecek diğer görevleri gösterir.

- Aşağıdaki seçeneklerden birini kullanarak Azure'daki ASP.NET uygulamanız için sanal bir makine oluşturun:
  - [ASP.NET Uygulamaları için yeni bir sanal makine oluşturun](https://go.microsoft.com/fwlink/?linkid=863237)
  - [Mevcut bir şirket içi VMWare sanal makineyi geçirin](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [Varolan bir şirket içi Hyper-V sanal makineyi geçirme](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [Visual Studio'u kullanarak uygulamanızı yayımlayın](https://go.microsoft.com/fwlink/?linkid=863240)
- [Sanal Müşterileriniz için güvenli bir sanal ağ oluşturun](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [Uygulamanız için bir CI/CD ardışık](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [Yüksek kullanılabilirlik ve ölçeklenebilirlik için VM ölçeğine geçme](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>Dikkat edilmesi gerekenler

### <a name="benefits"></a>Avantajlar

Sanal makineler, bir uygulamayı şirket içinde buluta geçirmek için en kolay yolu sunar. Uygulamanızın şirket içinde kullandığı ortamı çoğaltmanızı sağlarken, kendi veri merkezlerinizi koruma gereksinimini de ortadan kaldırır. Sanal Makine Ölçek Setleri, Sanal Makinelerde çalışan uygulamalar için yüksek kullanılabilirlik ve ölçeklenebilirlik sağlar.

### <a name="virtual-machine-size"></a>Sanal Makine Boyutu

İş yükünüz için en iyi şekilde optimize edilmiş sanal makine boyutunu ve türünü seçin. Daha fazla bilgi [için Azure'daki Windows sanal makineleri için Boyutlar'a](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)bakın.

### <a name="maintenance"></a>Bakım

Şirket içi bir makine gibi, sanal makineyi korumak ve<sup> güncellemekten&#42;. </sup> [Uygulamanız, Azure Uygulama Hizmeti](https://docs.microsoft.com/azure/app-service/) gibi bir Platform (PaaS) ortamında veya bir [kapsayıcıda](https://docs.microsoft.com/azure/app-service/containers/)çalıştırılabiliyorsa, bu gereksinimi ortadan kaldırır.

*<sup>sanal </sup>makine ölçek kümeleri için&#42;[Otomatik İşletim Sistemi yükseltmeleri](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) şu anda önizleme hizmeti olarak kullanılabilir.*

### <a name="virtual-networks"></a>Sanal Ağlar

Azure Sanal Ağlar şunları yapmanızı sağlar:

- Kontrol ettiğiniz karma bir altyapı oluşturun
- Kendi IP adreslerinizi ve DNS sunucularınızı getirin
- Uygulamalarınız için yalıtılmış ve son derece güvenli bir ortam oluşturun
- Birkaç [bağlantı seçeneğinden](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) birini kullanarak VM'nizi şirket içi ağınıza bağlayın
- [ExpressRoute'u](https://azure.microsoft.com/services/expressroute/) kullanarak sanal makinenizi şirket içi ağınıza entegre edin

Başlamak için Sanal [Ağ belgelerine](https://docs.microsoft.com/azure/virtual-network/) bakın

### <a name="active-directory"></a>Active Directory
Birçok uygulama kimlik doğrulama ve kimlik yönetimi için Active Directory kullanın.

- Azure AD Connect, şirket içi dizinlerinizi Azure Etkin Dizini ile tümleştirmenize olanak tanır. Başlamak için bkz. [Şirket içi dizinlerinizi Azure Etkin Dizini ile tümleştirin.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- Alternatif olarak, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) uygulamanızın şirket içi Active Directory'nize erişmesini sağlar.

### <a name="sql-databases"></a>SQL Veritabanları

Uygulamanız şirket içi bir veritabanı kullanıyorsa, uygulamanız varsayılan olarak uygulamayla konuşamaz. Şunlardan birini yapabilirsiniz:

- Uygulamanızın şirket içinde çalışan veritabanınıza erişmesini sağlayan karma bir ağ yapılandırın.
- Veritabanınızı Azure'a geçirin. Daha fazla bilgi için [bkz.](sql.md)

### <a name="high-availability-and-scalability"></a>Yüksek Kullanılabilirlik ve Ölçeklenebilirlik

#### <a name="virtual-machine-scale-sets"></a>Sanal Makine Ölçek Kümeleri
Uygulamanızın yüksek oranda kullanılabilir olduğundan emin olmak istersiniz ve uygulamanızın kullanılabilirliğini ve ölçeklenebilirliğini artırmak için VM görüntünüzü ölçeklendirebilir, Azure Sanal Makine Ölçeği Seti'ne geçirebilirsiniz. VM Ölçek Setleri, uygulamanızla birlikte bir görüntü oluşturmak için önceden yapılandırdığınız veya bir yapı ardışık hattı oluşturduğunuz varolan vm'yi kullanma olanağı sağlar.

Başlamak için bkz: [Uygulamanızı sanal makine ölçeği kümelerinde dağıtın.](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

#### <a name="centralized-logging"></a>Merkezi Ağaç Kesimi
Uygulamanızı birden çok örnekte çalıştırırken, günlüklerinizi [Azure Depolama](https://docs.microsoft.com/azure/storage/)gibi merkezi bir konumda depolamayı düşünün.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Azure’a SQL Server veritabanını geçirme](sql.md)
