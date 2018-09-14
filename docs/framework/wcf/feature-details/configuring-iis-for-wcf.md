---
title: Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521377"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma

Internet Information Services (IIS) 7.0 seçmeli olarak gerekli olan bileşenler yüklemenize olanak sağlayan modüler bir tasarım sahiptir. Bu tasarım, sunulan yeni bildirim temelli temsilinde teknolojisi dayalı [!INCLUDE[wv](../../../../includes/wv-md.md)]. 40'tan fazla tek başına özelliği bileşenleri bağımsız olarak yüklenebilir bir IIS 7.0 vardır. Bu, BT uzmanları yüklemenin gerekli kolayca özelleştirmenizi sağlar. Bu konuda, IIS 7.0, Windows Communication Foundation (WCF) ile kullanım için yapılandırın ve hangi bileşenlerin gerektiğini belirlemek nasıl ele alınmaktadır.

## <a name="minimal-installation-installing-was"></a>En düşük düzeyde yükleme: WAS yükleme
 Windows İşlem Etkinleştirme Hizmeti (WAS) tüm IIS 7.0 paketin en düşük düzeyde yükleme yüklemektir. Tek başına bir özellik olan ve yalnızca tüm kullanılabilir IIS 7.0 özellikten olan [!INCLUDE[wv](../../../../includes/wv-md.md)] işletim sistemleri (Home Basic, Home Premium, iş ve Ultimate ve Enterprise).

 Denetim Masası'ndan tıklayın **programlar** ve ardından **kapatma Windows özelliklerini aç veya Kapat** altında listelenen **programlar ve Özellikler**, WAS bileşen gösterilir Aşağıdaki resimde olduğu gibi liste.

 ![Özelliklerini açma veya kapatma iletişim](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Bu özellik aşağıdaki alt bileşenlere sahiptir:

-   .NET ortamı

-   Yapılandırma API'leri

-   İşlem modeli

 Yalnızca kök düğümünü WAS, seçerseniz **işlem modeli** alt düğümünde, varsayılan olarak denetlenir. Bir Web sunucusu desteği olduğundan bu yükleme işlemine yalnızca WAS, yüklemekte olduğunuz olduğunu lütfen unutmayın.

 WCF veya herhangi bir ASP.NET uygulaması iş yapmak için kontrol **.NET ortamını** onay kutusu. Bu, WAS bileşenlerinin tümünü WCF ve ASP.NET iyi çalışması için gerekli olduğu anlamına gelir. Bu bileşenlerden birini yükledikten sonra bu otomatik olarak denetlenir.

## <a name="iis-70-default-installation"></a>IIS 7.0: Varsayılan yükleme
 Denetleyerek **Internet Information Services** özelliğini, alt düğümlerinden bazıları aşağıdaki çizimde gösterildiği gibi otomatik olarak denetlenir.

 ![IIS 7.0 özellikleri için varsayılan ayarlar](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 IIS 7.0, bu varsayılan yüklemedir. Bu yükleme işlemine hizmet statik içerik (örneğin, HTML sayfaları ve diğer içerik) için IIS 7.0 kullanabilirsiniz. Ancak, ASP.NET veya CGI uygulaması veya WCF hizmetlerini barındırmak çalıştıramazsınız.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0: ASP.NET desteği yükleme
 ASP.NET IIS 7.0 üzerinde çalışır hale getirmek için ASP.NET yüklemeniz gerekir. Denetledikten sonra **ASP.NET**, ekranınızın aşağıdaki gibi görünmelidir.

 ![Asp.NET gerekli ayarları](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 IIS 7. 0'çalışması hem WCF ve ASP.NET uygulamaları için en az ortamı budur.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0: IIS 6.0 Uyumluluk bileşenlerini yüklemeyle
 IIS 7.0, Visual Studio 2005 veya bazı diğer Otomasyon betikleri ya da IIS 6.0 metatabanı API kullanan sanal uygulamaları yapılandırma araçları (örneğin, Adsutil.vbs) bir sistemde yüklerken, IIS 6.0 kontrol etmenizi sağlamak **komut dosyası oluşturma araçları**. IIS 6.0 diğer alt düğümlerini otomatik olarak denetler **Yönetim uyumluluğu**. Bunu yaptıktan sonra aşağıdaki çizim ekran gösterir:

 ![IIS 6.0 Yönetim uyumluluk ayarları](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Bu yükleme ile IIS 7.0, ASP.NET ve WCF özellikler ve örnekler kullanılabilir Web üzerinde kullanmak için gereken her şeye sahip.

## <a name="request-limits"></a>İstek sınırları
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] IIS 7'in varsayılan değer, `maxUri` ve `maxQueryStringSize` ayarları değiştirildi. İstek Filtreleme IIS 7. 0 ', varsayılan olarak, bir URL uzunluğu 4096 karakter ve bir sorgu dizesi uzunluğu 2048 karakter sağlar. Değiştirmek için bu varsayılan, App.config dosyanıza aşağıdaki XML'i ekleyin.

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a>Ayrıca Bkz.

- [WAS Etkinleştirme Mimarisi](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [WAS'ı WCF ile Kullanmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
