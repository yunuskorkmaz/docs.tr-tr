---
title: Windows Communication Foundation Örneklerini Çalıştırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2aca4555277a1b365ddee1c672a6375edfde9f34
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="running-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örneklerini Çalıştırma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Örnekleri tek makineli veya makine bazındaki bir yapılandırmada çalıştırılabilir. Sağlanan gibi örnekleri tek bir makinede çalıştırmak için hazır olursunuz. Çapraz makine yapılandırması, bir örnek ait yapılandırma dosyası ayarları değiştirmek gereklidir. Aşağıdaki yordamlarda bir örneği aynı makineye ve çapraz makine yapılandırmalarını çalıştırma açıklanmaktadır. Internet Information Services (IIS) ve kendi kendini barındıran örnekleri barındırılan hizmetler için adımları Çeşitlemeler olduğuna dikkat edin. Çoğu örnekleri IIS'de barındırılan; nasıl barındırılan belirlemek için örnek Benioku bilgilere bakın.  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], IIS'de barındırılan değil örnekleri bir dinleyici Http.sys ile kaydetmek için yükseltilmiş ayrıcalıklar gerektirir. Httpcfg.exe hizmetinin altında çalıştığı hesabın ile hizmetin dinleme adreslerini kaydetmek için kullanın ya da yönetici ayrıcalıklarıyla çalışan bir komut isteminden hizmeti başlatın.  
  
> [!NOTE]
>  Derleme veya herhangi birini çalıştıran önce [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri, gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aynı makinede örneği çalıştırmak için  
  
1.  IIS tarafından barındırılan hizmetindeki, hizmeti aşağıdaki adresini girerek bir tarayıcı kullanarak erişebildiğinden emin olun: http://localhost/servicemodelsamples/service.svc. Bir onay sayfasına yanıtta görüntülenmesi gerekir. Onay sayfasında görüntülenmiyorsa bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Hizmet kendi kendine barındırılıyorsa Service.exe dile özgü klasörü altında \service\bin çalıştırın. Hizmet etkinliğinin hizmet konsol penceresinde görüntülenir.  
  
3.  \Client\bin Client.exe çalıştırmak\\, dile özgü klasörü altında. İstemci etkinliği istemci konsol penceresi görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Makine genelinde örneği çalıştırmak için  
  
1.  IIS'de barındırılan hizmetindeki ise:  
  
    1.  Hizmeti makinede ServiceModelSamples adlı bir sanal dizin oluşturun. Setupvroot.bat bulunan toplu iş dosyası [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizini oluşturmak için kullanılabilir.  
  
    2.  Hizmet program dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizine kopyalayın. \Bin dizindeki dosyaları eklediğinizden emin olun.  
  
    3.  Test, hizmet bir tarayıcı kullanarak istemci makineden erişebilirsiniz.  
  
     Hizmet kendiliğinden barındırılır ise:  
  
    1.  Hizmeti makinede hizmet dosyalarını barındıracak bir dizin oluşturun.  
  
    2.  Hizmet program dosyalarını \service\bin\ klasöründen dile özgü klasörü altında hizmet makineye kopyalayın.  
  
    3.  Hizmet yapılandırma dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin. Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.  
  
    4.  Bir komut isteminden Service.exe başlatın.  
  
2.  İstemci makine dile özgü klasörü altındaki \client\bin\ klasöründen istemci program dosyaları kopyalayın.  
  
3.  Uç nokta adresi ayarlayın.  
  
    1.  Hizmeti bir etki alanı hesabı altında çalışır değilse, istemci yapılandırma dosyasını açın ve yeni adresi hizmetinizin eşleştirmek için uç nokta tanımı adresi değerini değiştirin. Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.  
  
    2.  Hizmeti bir etki alanı hesabı altında çalışıyorsa, istemci yapılandırması karşı hizmet Svcutil.exe çalıştırarak yeniden oluşturun. Svcutil.exe çalıştırma hakkında daha fazla bilgi için bkz: [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md). Örnek yapılandırma dosyasında yerine oluşturulan dosyasını kullanın. Oluşturulan yapılandırma dosyası, ek kimlik bilgileri olan ve varsayılan ayarları olsa bile hizmet uç noktasına bağlanmak gerekli tüm ayarları içerir. Kimlik bilgileri hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), ve [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  İstemci makinesinde, bir komut isteminden Client.exe başlatın.  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1.  Yapı Çözümü (istemci ve hizmet) kullanarak **yapı** menüsü veya CTRL + SHIFT + B.  
  
2.  IIS'de barındırılan hizmetindeki ise:  
  
    1.  Adresini girerek bir tarayıcı kullanarak hizmetini etkinleştirme http://localhost/servicemodelsamples/service.svc.  
  
    2.  Çözümde seçin **hata ayıklama** menü ve **ekleme işlemi için** menü öğesi.  
  
    3.  Seçin **işlemleri tüm kullanıcıları göster** onay kutusu.  
  
    4.  Ana çalışan işlem hatalarını ayıklamak için W3wp.exe seçin (Windows XP ASPNet_wp.exe seçin).  
  
3.  Şimdi hizmet kodunda kesme noktalarını ayarlayın ve özel durumları üzerinde kesme noktaları etkinleştirin.  
  
4.  İstemci proje öğesi sağ tıklatın ve seçin **hata ayıklama**, **başlangıç yeni örnek**.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Hizmet güvenlik nedenleriyle IIS'de barındırılıyorsa, sanal dizin tanımı ve örnekleri ile işiniz bittiğinde Kurulum adımlarında'ı izinler kaldırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation Örnekleri Derleme](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Bir çalışma grubunda ve makinelerde örneklerini çalıştırma](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [Sorun Giderme İpuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
