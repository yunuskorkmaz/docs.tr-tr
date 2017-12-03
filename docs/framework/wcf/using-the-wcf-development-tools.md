---
title: "WCF Geliştirme Araçlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9532363adafd492ca35e10e6d20c788ddf5b1d17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-wcf-development-tools"></a>WCF Geliştirme Araçlarını Kullanma
Bu bölümde açıklanmıştır [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] geliştirmeye yardımcı olabilecek geliştirme araçları, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]hizmeti.  
  
 Kullanabilirsiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hızlı bir şekilde kendi hizmet oluşturmak için bir temel olarak şablonları kullanın. ardından [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti otomatik ana bilgisayarı ve [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci hata ayıklama ve hizmetinizi test etmek için Test. Bu araçları birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsü sağlar ve barındırma modeli için erken bir aşamada yürütmek için gereken engellemek.  
  
## <a name="the-wcf-developer-tools"></a>WCF geliştirici araçları  
 [WCF Visual Studio şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Kullanabileceğiniz önceden tanımlanmış [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] proje ve öğe şablonlarını [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hızlı bir şekilde oluşturmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetler ve çevresindeki uygulamalar.  
  
 [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmeti otomatik ana bilgisayarı (WcfSvcHost.exe) başlatmak verir [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hata ayıklayıcı otomatik olarak ana bilgisayar ve uygulanan bir hizmeti test (F5). Hizmetini kullanarak sınayabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi (wcfTestClient.exe) veya kendi istemci bulmak ve olası hataları düzeltmek için.  
  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Test İstemcisi (WcfTestClient.exe) giriş parametreleri rastgele türler, hizmet ve hizmet yanıtı geri gönderir görünümü için giriş göndermek izin veren bir GUI aracıdır. İle birleştirildiğinde deneyimi sınama sorunsuz bir hizmet sunar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti otomatik ana bilgisayarı.  
  
 [XML'den veri türü sınıfları oluşturma](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 XML verileri Pano'ya depolanan bir kod sayfasına yapıştırılabilmesi için. Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Yönetici ayrıcalığı olmadan araçlarını kullanma  
 Geliştirmek için yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri, bir ACL (erişim denetim listesi) oluşturulur "http://+:8731/Design_Time_Addresses" ad alanı için yüklemesi sırasında [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. ACL hangi makineye oturum açmış etkileşimli kullanıcıların tümünü içerir (UI) ayarlanır. Yöneticiler eklemek veya bu ACL'den kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL varsayılan yapılandırmalarında veri alıp göndermek WCF veya WF şablonları sağlar. Ayrıca, kullanıcıların kullanmasını sağlar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet otomatik yönetici ayrıcalıklarını verme olmadan Konağı (wcfSvcHost.exe).  
  
 Erişim Netsh.exe aracını kullanarak değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında. Netsh.exe kullanmaya ilişkin bir örnek verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Netsh.exe, bkz: [Netsh.exe aracı ve komut satırı anahtarları kullanmayı](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Visual Studio şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
