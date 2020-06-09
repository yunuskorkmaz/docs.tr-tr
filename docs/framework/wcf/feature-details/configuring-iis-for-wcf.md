---
title: Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 6343049e2a21b06965a8c7851d891303a49c82b5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597572"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma

Internet Information Services (IIS) 7,0, gereken bileşenleri seçmeli olarak yüklemenize olanak sağlayan modüler bir tasarıma sahiptir. Bu tasarım, Windows Vista 'da tanıtılan yeni bildirim temelli bileşen teknolojisini temel alır. IIS 7,0 ' ün bağımsız olarak tek başına yüklenebilen 40 ' den fazla bağımsız Özellik bileşeni vardır. Bu, BT uzmanlarının yüklemeyi gerektiği şekilde kolayca özelleştirmesini sağlar. Bu konuda, IIS 7,0 ' ü Windows Communication Foundation (WCF) ile kullanım için yapılandırma ve hangi bileşenlerin gerekli olduğunu belirleme konusu ele alınmaktadır.

## <a name="minimal-installation-installing-was"></a>En az yükleme: yükleme WAS
 Tüm IIS 7,0 paketinin en düşük yüklemesi, Windows Işlem etkinleştirme hizmeti 'ni (WAS) yüklemektir. , Tek başına bir özelliktir ve IIS 7,0 ' den tüm Windows Vista işletim sistemleri (Home Basic, Home Premium, Business ve Ultimate ve Enterprise) için kullanılabilen tek özelliktir.

 Denetim Masası ' nda, **Programlar** ' a ve ardından **Programlar ve Özellikler**altında listelenen **Windows özelliklerini aç veya kapat** ' a tıklayın, aşağıdaki çizimde gösterildiği gibi, was bileşeni listede gösterilir.

 ![Özellikleri aç veya kapat Iletişim kutusu](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Bu özellik aşağıdaki alt bileşenlere sahiptir:

- .NET ortamı

- Yapılandırma API 'Leri

- İşlem modeli

 WAS kök düğümünü seçerseniz, yalnızca **Işlem modeli** alt düğümü varsayılan olarak denetlenir. Lütfen bu yüklemede, Web sunucusu için destek bulunmadığından emin olun.

 WCF veya ASP.NET uygulamasının çalışmasını sağlamak için **.net ortamı** onay kutusunu işaretleyin. Bu, WCF ve ASP.NET 'in düzgün çalışmasını sağlamak için tüm WAS bileşenlerinin gerekli olduğu anlamına gelir. Bunlar, bu bileşenlerden herhangi birini yükledikten sonra otomatik olarak denetlenir.

## <a name="iis-70-default-installation"></a>IIS 7,0: varsayılan yükleme
 **Internet Information Services** özelliğini denetleyerek, bazı alt düğümlerden bazıları aşağıdaki çizimde gösterildiği gibi otomatik olarak denetlenir.

 ![IIS 7,0 özellikleri için varsayılan ayarlar](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Bu, varsayılan IIS 7,0 yüklemesidir. Bu yüklemeyle, IIS 7,0 kullanarak statik içeriğe (örneğin, HTML sayfaları ve diğer içerikler) hizmet sağlayabilirsiniz. Ancak, ASP.NET veya CGI uygulamalarını çalıştıramazsınız veya WCF hizmetlerini barındırabilirsiniz.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7,0: ASP.NET desteğiyle yükleme
 IIS 7,0 üzerinde ASP.NET çalışması yapmak için ASP.NET yüklemelisiniz. **ASP.net**denetledikten sonra, ekranınız aşağıdaki şekilde görünmelidir.

 ![Gerekli Asp.NET ayarları](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Bu, hem WCF hem de ASP.NET uygulamalarının IIS 7,0 ' de çalışması için en düşük ortamdır.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7,0: IIS 6,0 uyumluluk bileşenleriyle yükleme
 IIS 7,0 ' i Visual Studio 2005 içeren bir sisteme veya IIS 6,0 metatabanı API 'SI kullanan sanal uygulamaları yapılandıran başka bazı Otomasyon betikleri ya da araçlarına (adsutil. vbs gibi) yüklerken IIS 6,0 **Scripting araçları**' nı denetletdiğinizden emin olun. Bu, IIS 6,0 **Yönetim uyumluluğun**diğer alt düğümlerini otomatik olarak denetler. Aşağıdaki çizimde, Bu yapıldıktan sonra ekran gösterilmektedir:

 ![IIS 6,0 yönetimi uyumluluk ayarları](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Bu yüklemeyle, Web 'de bulunan IIS 7,0, ASP.NET ve WCF özelliklerini ve örneklerini kullanmak için gereken her şey vardır.

## <a name="request-limits"></a>İstek sınırları
 IIS 7 ile Windows Vista 'da, ve ayarlarının varsayılan değeri `maxUri` `maxQueryStringSize` değiştirilmiştir. Varsayılan olarak, IIS 7,0 ' de istek filtreleme, 4096 karakterlik bir URL uzunluğu ve bir sorgu dizesi uzunluğu olan 2048 karakter olarak izin verir. Bu Varsayılanları değiştirmek için aşağıdaki XML 'i App. config dosyanıza ekleyin.

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>Ayrıca bkz.

- [WAS Etkinleştirme Mimarisi](was-activation-architecture.md)
- [WAS'ı WCF ile Kullanmak için Yapılandırma](configuring-the-wpa--service-for-use-with-wcf.md)
- [Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma](how-to-install-and-configure-wcf-activation-components.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
