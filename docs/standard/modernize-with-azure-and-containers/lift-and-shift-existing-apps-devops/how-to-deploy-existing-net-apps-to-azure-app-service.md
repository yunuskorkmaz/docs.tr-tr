---
title: "Azure App Service'e varolan .NET uygulamalarını dağıtma"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Azure App Service'e varolan .NET uygulamalarını dağıtma"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84bffe7aad6bbffb40519c9146d8156159d55850
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>Azure App Service'e varolan .NET uygulamalarını dağıtma 

Azure App Service Web Apps özelliğini Web sitelerini ve web uygulamalarını barındırmak için iyileştirilmiş bir tam olarak yönetilen bir işlem platformudur. Microsoft Azure sağlar, bu PaaS teklifi Azure alır çalıştırmak ve uygulamalarınızı ölçeklendirmek için altyapınızla ilgilenirken, iş mantığına odaklanın.

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>Siteleri doğrulamak ve Azure App Service geçiş Yardımcısı ile App Service'e geçirme

Visual Studio, uygulama için uygulama hizmeti genellikle taşıma yeni bir uygulama oluşturduğunuzda basittir. Uygulama hizmeti varolan bir uygulamaya geçirmeyi planlıyorsanız, ancak öncelikle tüm uygulama bağımlılıklarını App Service ile uyumlu olup olmadığını değerlendirmek gerekir. Bu, sunucu işletim sistemi ve sunucuda yüklü herhangi bir üçüncü taraf yazılım gibi bağımlılıkları içerir.

Kullanabileceğiniz [Azure App Service geçiş Yardımcısı](https://www.migratetoazure.net/) siteleri çözümlemek ve bunları Windows ve Linux web sunucularından App Service'e geçirme. Geçiş işleminin bir parçası olarak aracı, web uygulamaları oluşturur ve Azure veritabanlarında gerektiği gibi içeriği yayımlar ve veritabanınızı yayımlar.

Azure uygulama hizmeti geçiş Yardımcısı buluta Windows Server'da çalışan IIS geçiş destekler. Uygulama hizmeti, Windows Server 2003 ve sonraki sürümleri destekler.

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> **Şekil 4-5.** Azure uygulama hizmeti geçiş Yardımcısını kullanma

Uygulama hizmeti geçiş Yardımcısı, Web siteleri, web sunucularından Azure bulut taşınan bir araçtır.

Bir Web sitesi için uygulama hizmeti geçirildikten sonra site güvenli ve verimli bir şekilde çalışması için gereken her şeyi içerir. Siteleri ayarlamak ve otomatik olarak Azure bulut PaaS hizmeti (uygulama hizmeti) çalıştırın.

Uygulama hizmeti geçiş aracı, Web sitelerinizi çözümleyebilir ve App Service'e taşıma için kendi uyumluluğu hakkında rapor oluşturun. Analizi ile memnun kaldıysanız, App Service geçiş içerik, veriler ve ayarlar, geçiş Yardımcısı izin verebilirsiniz. Bir site oldukça uyumlu değilse, geçiş aracının çalışması için ayarlamak gerekenleri açıklar.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Azure uygulama hizmeti geçiş Yardımcısı**

    [https://www.migratetoazure.net/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[Önceki](what-about-cloud-optimized-applications.md)
[sonraki](deploy-existing-net-apps-as-windows-containers.md)
