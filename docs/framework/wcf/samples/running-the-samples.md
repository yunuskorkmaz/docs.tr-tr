---
title: Windows Communication Foundation Örneklerini Çalıştırma
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: f2d28ac8c1cfc13a8d2f17c9d4e1bcc92cf559e3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664740"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örneklerini Çalıştırma
Windows Communication Foundation (WCF) örnekleri, tek bir makine veya çapraz makine yapılandırmada çalıştırabilirsiniz. Sağlanan olarak örnekler tek bir makinede çalıştırmak için hazır olursunuz. Çapraz makine yapılandırması, bir örnek 's yapılandırma dosyası ayarları değiştirmek gereklidir. Aşağıdaki yordamlarda, aynı makineye ve çapraz makine yapılandırmaları bir örnek çalıştırmak açıklanmaktadır. Internet Information Services (IIS) ve şirket içinde barındırılan örnekleri barındırılan hizmetler için adımları farklılığı olduğunu unutmayın. Çoğu örnekleri IIS'de barındırılan; nasıl barındırılan belirlemek için örnek Benioku bilgilere bakın.  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], IIS'de barındırılmamaktadır örnekleri bir dinleyici Http.sys ile kaydolmak için yükseltilmiş ayrıcalıklar gerektirir. Hizmetin altında çalıştığı hesabın hizmet dinleme adreslerini kaydetmek için httpcfg.exe kullanın veya yönetici ayrıcalıklarıyla çalışan bir komut isteminden service'ı başlatın.  
  
> [!NOTE]
>  Oluşturma veya WCF örnekleri birini çalıştırmadan önce gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Hizmeti, IIS tarafından barındırılıyorsa, hizmeti aşağıdaki adresi girerek bir tarayıcı kullanarak erişebildiğinden emin olun: `http://localhost/servicemodelsamples/service.svc`. Yanıtta bir onay sayfası gösterilmelidir. Onay sayfasında görüntülenmiyorsa bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
2. Hizmet şirket içinde barındırılıyorsa Service.exe \service\bin, dile özgü klasörü altında çalıştırın. Hizmet etkinliğinin hizmet konsol penceresinde görüntülenir.  
  
3. \Client\bin Client.exe çalıştırma\\, dile özgü klasörü altında. İstemci etkinliği istemci konsol penceresinde görüntülenir.  
  
4. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Makineler arasında örneği çalıştırmak için  
  
1. Hizmet IIS'de barındırılıyorsa:  
  
    1. Hizmeti makinede ServiceModelSamples adlı sanal bir dizin oluşturun. Toplu iş dosyasını Setupvroot.bat bulunan [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizin oluşturmak için kullanılabilir.  
  
    2. Hizmet program dosyaları %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizinine kopyalayın. \Bin dizinine dosyaları eklediğinizden emin olun.  
  
    3. Test bir tarayıcı kullanarak istemci makine hizmete erişebilir.  
  
     Hizmet, şirket içinde barındırılan ise:  
  
    1. Hizmeti makinede hizmet dosyalarını tutmak için bir dizin oluşturun.  
  
    2. Hizmet program dosyaları \service\bin\ klasöründen, dile özgü klasörü altında hizmet makineye kopyalayın.  
  
    3. Hizmet yapılandırma dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
    4. Service.exe, bir komut istemi'nden başlatın.  
  
2. İstemci program dosyaları \client\bin\ klasöründen, dile özgü klasörünün altındaki istemci makineye kopyalayın.  
  
3. Uç nokta adresini ayarlayın.  
  
    1. Bir etki alanı hesabı altında hizmet çalışmıyorsa, istemci yapılandırma dosyasını açın ve adres uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
    2. İstemci Yapılandırma hizmeti bir etki alanı hesabı altında çalışıyorsa, hizmete yönelik Svcutil.exe çalıştırarak yeniden oluşturun. Svcutil.exe çalıştırma hakkında daha fazla bilgi için bkz. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md). Örnek yapılandırma dosyasında yerine üretilen dosyayı kullanın. Oluşturulan yapılandırma dosyası, ek kimlik bilgileri ve varsayılan ayarları olsa bile hizmet uç noktaya bağlanmak için gereken tüm ayarları içerir. Kimlik bilgileri hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), ve [ \<kimlik >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4. İstemci makinesinde bir komut istemi'nden Client.exe başlatın.  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1. Çözüm (hem istemci hem de hizmet) kullanarak derleme **derleme** menüsünden veya CTRL + SHIFT + B.  
  
2. Hizmet IIS'de barındırılıyorsa:  
  
    1. Adresini girerek bir tarayıcı kullanarak hizmeti etkinleştirin `http://localhost/servicemodelsamples/service.svc`.  
  
    2. Çözümde seçin **hata ayıklama** menü ve **iliştirme** menü öğesi.  
  
    3. Seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.  
  
    4. Konak çalışan işlem hatalarını ayıklamak için W3wp.exe seçin (Windows XP ASPNet_wp.exe seçin).  
  
3. Şimdi, hizmet kodda kesme noktaları ayarlayın ve özel durumlar üzerinde kesme noktalarını etkinleştir.  
  
4. İstemci projesine sağ tıklayın ve seçin **hata ayıklama**, **yeni örnek Başlat**.  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
- Hizmet, güvenlik nedenleriyle IIS'de barındırılıyorsa, sanal dizin tanımını ve örneklerle tamamladığınızda Kurulumu adımları verilen izinler kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Örnekleri Derleme](../../../../docs/framework/wcf/samples/building-the-samples.md)
- [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
