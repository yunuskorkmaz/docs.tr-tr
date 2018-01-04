---
title: "Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 511f5177e1b9d2660daf887cc13728aed2c9de0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma
Internet Information Services (IIS) 7.0 gerekli bileşenleri seçerek yüklemenize olanak tanıyan bir modüler tasarımı vardır. Bu tasarım, içinde sunulan yeni bildirim temelli temsilinde teknolojisini temel [!INCLUDE[wv](../../../../includes/wv-md.md)]. 40'tan fazla tek başına özelliği bileşenleri vardır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] , yüklenebilir bağımsız olarak. Bu, BT uzmanları kolayca yüklemesini gerektiği gibi özelleştirin sağlar. Bu konuda nasıl yapılandırılacağı açıklanır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ile kullanılmak üzere [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve hangi bileşenler gereklidir belirleyin.  
  
## <a name="minimal-installation-installing-was"></a>: En az WAS yüklemesi  
 Bütün en düşük düzeyde yükleme [!INCLUDE[iisver](../../../../includes/iisver-md.md)] paketidir Windows İşlem Etkinleştirme Hizmeti (WAS) yüklemek için. Tek başına bir özellik olan ve yalnızca özelliğinden olan [!INCLUDE[iisver](../../../../includes/iisver-md.md)] tüm kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)] işletim sistemleri (Home Basic, Home Premium, iş ve Ultimate ve Enterprise).  
  
 Denetim Masası'ndan tıklatın **programları** ve ardından **kapatma Windows özelliklerini aç veya Kapat** altında listelenen **programlar ve Özellikler**, WAS bileşen gösterilir Aşağıdaki çizimde olduğu gibi listesi.  
  
 ![Özelliklerini açmak veya kapatmak iletişim](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 Bu özellik aşağıdaki alt bileşene sahiptir:  
  
-   .NET ortamı  
  
-   Yapılandırma API'leri  
  
-   İşlem modeli  
  
 Yalnızca kök düğümü WAS, seçerseniz **işlem modeli** alt düğümü varsayılan olarak işaretli. Bir Web sunucusu desteği olduğundan lütfen bu yükleme işlemine yalnızca WAS, yüklemekte olduğunuz olduğunu unutmayın.  
  
 Yapmak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya tüm [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamanın çalışması için denetleyin **.NET ortamı** onay kutusu. WAS bileşenlerinin tümünü yapmak için gereklidir yani [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] düzgün çalışması için. Bu bileşenler birini yükledikten sonra bunlar otomatik olarak denetlenir.  
  
## <a name="iis-70-default-installation"></a>IIS 7.0: Varsayılan yükleme  
 Denetleyerek **Internet Information Services** özelliği, bazı alt düğümler aşağıdaki çizimde gösterildiği gibi otomatik olarak denetlenir.  
  
 ![IIS 7.0 özellikler için varsayılan ayarlar](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 Bu, varsayılan yüklemedir [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Bu yükleme işlemine kullandığınız [!INCLUDE[iisver](../../../../includes/iisver-md.md)] hizmet statik içerik (örneğin, HTML sayfaları ve diğer içeriği). Ancak, çalıştıramazsınız [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya CGI uygulamaları ya da konak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.  
  
## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0: ASP.NET desteğiyle yükleme  
 Yüklemelisiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yapmak için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] IIS 7.0 üzerinde çalışır. Denetledikten sonra **ASP.NET**, ekranınızda aşağıdaki gibi görünmelidir.  
  
 ![Asp.NET gerekli ayarları](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 Bu her ikisi için de en az ortamıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] iş uygulamaları [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0: IIS 6.0 Uyumluluk bileşenleri ile yükleme  
 Yükleme sırasında [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Visual Studio 2005 veya bazı diğer Otomasyon betikleri veya kullanan sanal uygulamaları yapılandırma araçları (örneğin, Adsutil.vbs) sahip bir sistemde [!INCLUDE[iis601](../../../../includes/iis601-md.md)] metatabanı API, olun işaretlemeniz özellikle [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **Komut dosyası araçları**. Bu diğer alt düğümlerin otomatik olarak denetler [!INCLUDE[iis601](../../../../includes/iis601-md.md)] **Yönetim uyumluluğu**. Bu yapıldıktan sonra ekran aşağıda gösterilmektedir.  
  
 ![IIS 6.0 Yönetim uyumluluk ayarları](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 Bu yükleme işlemine kullanmak için gereken her şeyi elinizde [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özellikleri ve örnek Web üzerinde kullanılabilir.  
  
## <a name="request-limits"></a>İstek sınırları  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] IIS 7'in varsayılan değer, `maxUri` ve `maxQueryStringSize` ayarları değiştirildi. Varsayılan olarak, istek IIS 7. 0 ' filtreleme, URL uzunluğu 4096 karakter ve bir sorgu dizesi uzunluğu 2048 karakter sağlar. Değiştirmek için bu varsayılan aşağıdaki XML App.config dosyasına ekleyin.  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WAS Etkinleştirme Mimarisi](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [WAS'ı WCF ile Kullanmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
