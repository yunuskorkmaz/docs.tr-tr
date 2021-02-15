---
title: Dağıtım stratejileri
description: ASP.NET 'den ASP.NET Core 'e geçiş yaparken takımlar hangi dağıtım stratejilerini kullanabilir? Artımlı bir geçiş, .NET Framework ve .NET Core uygulamalarının yan yana dağıtımına izin vererek sorunsuz bir son kullanıcı deneyimi sağlar mi?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 85797ed0003e7dd2f53fad3b51876ae1cf01b0ba
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488902"
---
# <a name="deployment-strategies"></a>Dağıtım stratejileri

Büyük ASP.NET uygulamanızın geçişini planlarken, yeni uygulamayı nasıl dağıtacağınızı ASP.NET Core bir göz önünde bulundurun. ASP.NET ile dağıtım seçenekleri Windows üzerinde IIS ile sınırlandırılmıştır. ASP.NET Core, dağıtım seçenekleri için çok daha geniş bir dizi vardır.

## <a name="cross-platform-options"></a>Platformlar arası seçenekler

.NET Core, Linux üzerinde çalıştığından, daha önce dikkate almamakta olan bazı barındırma seçeneklerini bulabilirsiniz. Linux tabanlı barındırma aşağıdaki nedenlerle tercih edilebilir.

* Kuruluşunuzun altyapısı veya uzmanlığı vardır.
* Barındırma sağlayıcıları, Linux tabanlı barındırma için etkileyici özellikler veya fiyatlandırma sağlar.

.NET Core, bu seçeneklere yönelik olarak açılır.

## <a name="cloud-native-development"></a>Bulutta yerel geliştirme

Günümüzde çoğu kuruluş, en az bir yazılım özelliği için bulut platformları kullanıyor. .NET Core 'a uygulama geçişi sayesinde uygulamanın, bulut barındırmayla birlikte tam olarak yazılmış olması gerekip gerekmediğini göz önünde bulundurmanız iyi bir zamandır. Bu tür *bulut Yerel* uygulamalar sunucusuz, mikro hizmetler gibi bulut yeteneklerini uygulayabilir ve bunların nasıl ve nerede dağıtılabileceği konusunda düşük düzeyli ayrıntılarla daha az endişe sağlayabilir.

Bu ücretsiz e-kitapta Cloud Native uygulama geliştirme hakkında daha fazla bilgi edinin ve [Azure Için Cloud Native .NET uygulamaları tasarlayarak](/dotnet/architecture/cloud-native/).

## <a name="leverage-containers"></a>Kapsayıcılardan yararlanma

Modern uygulamalar genellikle, barındırma ortamları arasındaki değişimleri azaltmanın bir yolu olarak kapsayıcılardan yararlanır. Bir uygulamayı belirli bir kapsayıcıya dağıtarak, kapsayıcı tarafından barındırılan uygulama bir geliştiricinin dizüstü bilgisayarında veya üretimde çalışıp çalışmadığını aynı şekilde çalıştırır. .NET Core 'a geçişin bir parçası olarak, uygulamanın bir tam tek veya daha küçük Kapsayıcılı uygulamalara ayrılmış olarak kapsayıcı aracılığıyla dağıtımdan faydalanıp avantajına dikkat edebilir.

## <a name="side-by-side-deployment-options"></a>Yan yana dağıtım seçenekleri

Büyük .NET Framework uygulamalarının .NET Core 'a geçirilmesi, genellikle önemli bir çaba gerektirir. Çoğu kuruluş, tüm geçiş tamamlanmadan önce, uygulamanın parçalarının üretime geçirilmesi ve dağıtılması için bazı şekilde bu çabadan daha fazla bilgi sağlayabilmesini ister. Hem özgün ASP.NET uygulamasını hem de yeni geçirilen ASP.NET Core alt uygulamalarını yan yana çalıştırmak, genellikle alıntı yapılan bir hedeftir. Bu, [Bölüm 5](deployment-scenarios.md)' te ele alınan IIS yönlendirmesinin kullanılmasıyla birlikte çeşitli mekanizmalarla elde edilebilir. Diğer seçenekler, ASP.NET Web API 'leri ve ASP.NET Core API uç noktaları kümelerini yönetmek üzere ön [uçlar için arka uçları](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) gibi uygulama ağ geçitlerinin veya bulut Tasarım desenlerinin kullanımını içerir.

## <a name="iis-on-windows"></a>Windows üzerinde IIS

Uygulamalarınızı Windows üzerinde çalışan IIS 'de barındırmaya devam edebilirsiniz. Bu, geçerli dağıtım modellerini değiştirmeden ASP.NET Core özelliklerinden yararlanmak isteyen müşteriler için ince bir seçenektir. ASP.NET Core geçiş sırasında uygulamalarınızın nasıl ve nereye dağıtılacağı konusunda daha fazla seçenek sunurken, Windows üzerinde IIS 'nin kanıtlanmış birleşimini kullanarak Quo durumundan geçmeniz gerekmez.

## <a name="other-options-on-windows"></a>Windows üzerinde diğer seçenekler

Gerekirse, Docker kapsayıcılarına ek olarak, Kestrel, HTTP.sys ve IIS konaklarının herhangi bir birleşimini kullanarak Windows 'da yan yana uygulamalar barındırabilirsiniz. Uygulamanız Windows ve Linux hizmetlerinin bir birleşimini gerektiriyorsa, [WSL](https://docs.microsoft.com/windows/wsl/about) ve/veya Linux Docker Kapsayıcıları Içeren bir Windows Server üzerinde barındırma, uygulamanın tüm bölümlerini barındırmak için tek bir sunucu çözümü sağlar.

## <a name="references"></a>Başvurular

- [ASP.NET Core barındırma ve dağıtma](https://docs.microsoft.com/aspnet/core/host-and-deploy/)
- [IIS ile Windows üzerinde ASP.NET Core barındırma](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/)
- [Azure App Service ve IIS 'de ASP.NET Core sorunlarını giderme](https://docs.microsoft.com/aspnet/core/test/troubleshoot-azure-iis)

>[!div class="step-by-step"]
>[Önceki](migrate-web-forms.md) 
> [Sonraki](additional-migration-resources.md)
