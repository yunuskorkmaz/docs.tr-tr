---
title: Windows Communication Foundation Örneklerini Çalıştırma
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: 57f760fa8bf4a3abf83492ac455dfaed2b327e7e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545109"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örneklerini Çalıştırma
Windows Communication Foundation (WCF) örnekleri, tek makineli veya bir çapraz makine yapılandırmasında çalıştırılabilir. Sağlandığı gibi, örnekler tek bir makinede çalıştırılmaya hazırlardır. Bir çapraz makine yapılandırmasında, bir örneğin yapılandırma dosyası ayarlarını değiştirmek gereklidir. Aşağıdaki yordamlarda, aynı makine ve makineler arası yapılandırmalarda bir örneği çalıştırmanın açıklanmaktadır. Internet Information Services (IIS) ve şirket içinde barındırılan örneklerde barındırılan hizmetler için adımlarda Çeşitlemeler bulunduğunu unutmayın. Çoğu örnek IIS 'de barındırılır; nasıl barındırıldığını öğrenmek için örnek Benioku bilgilerine bakın.  
  
 Windows Vista 'da, IIS 'de barındırılmayan örnekler, Http.sys bir dinleyici kaydetmek için yükseltilmiş ayrıcalıklar gerektirir. Hizmetin dinleme adreslerini hizmetin altında çalıştığı hesapla kaydetmek veya hizmeti yönetici ayrıcalıklarıyla çalışan bir komut isteminden başlatmak için Httpcfg.exe kullanın.  
  
> [!NOTE]
> WCF örneklerinden herhangi birini oluşturmadan veya çalıştırmadan önce, [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Hizmet IIS tarafından barındırılıyorsa, şu adresi girerek hizmete bir tarayıcı kullanarak erişebildiğinizden emin olun: `http://localhost/servicemodelsamples/service.svc` . Yanıt olarak bir onay sayfası görüntülenmelidir. Onay sayfası görüntülenmiyorsa, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
2. Hizmet şirket içinde barındırılıyorsa, \ service\bin ' den dile özgü klasörden Service.exe çalıştırın. Hizmet etkinliği, hizmet konsolu penceresinde görüntülenir.  
  
3. \ Client\bin \\ ' den dile özgü klasörden Client.exe çalıştırın. İstemci etkinliği istemci konsol penceresinde görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Hizmet IIS 'de barındırılıyorsa:  
  
    1. Hizmet makinesinde, ServiceModelSamples adlı bir sanal dizin oluşturun. Toplu iş dosyası, [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamıyla](one-time-setup-procedure-for-the-wcf-samples.md) birlikte Setupvroot.bat disk dizini ve sanal dizin oluşturmak için kullanılabilir.  
  
    2. Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki ServiceModelSamples sanal dizinine kopyalayın. Dosyalarını \Bin dizinine dahil ettiğinizden emin olun.  
  
    3. Bir tarayıcı kullanarak hizmete istemci makineden erişebilme sınamasını yapın.  
  
     Hizmet kendi kendine barındırılıyorsa:  
  
    1. Hizmet makinesinde, hizmet dosyalarını tutacak bir dizin oluşturun.  
  
    2. Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet makinesine kopyalayın.  
  
    3. Hizmet yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
    4. Komut isteminden Service.exe başlatın.  
  
2. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.  
  
3. Uç nokta adresini ayarlayın.  
  
    1. Hizmet bir etki alanı hesabı altında çalışmıyorsa, istemci yapılandırma dosyasını açın ve uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
    2. Hizmet bir etki alanı hesabı altında çalışıyorsa, hizmete karşı Svcutil.exe çalıştırarak istemci yapılandırmasını yeniden oluşturun. Svcutil.exe çalıştırma hakkında daha fazla bilgi için bkz. [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md). Örnekteki yapılandırma dosyası yerine oluşturulan dosyayı kullanın. Oluşturulan yapılandırma dosyasında ek kimlik bilgileri bulunur ve varsayılan ayarlar olsalar bile hizmet uç noktasına bağlanmak için gerekli tüm ayarları içerir. Kimlik bilgileri hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md)ve [\<identity>](../../configure-apps/file-schema/wcf/identity.md) .  
  
4. İstemci makinesinde, bir komut isteminden Client.exe başlatın.  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1. **Build** menüsünü veya CTRL + SHIFT + B kullanarak çözümü (hem istemci hem de hizmet) oluşturun.  
  
2. Hizmet IIS 'de barındırılıyorsa:  
  
    1. Adresi girerek bir tarayıcı kullanarak hizmeti etkinleştirin `http://localhost/servicemodelsamples/service.svc` .  
  
    2. Çözümde **Hata Ayıkla** menüsünü ve **İşleme İliştir** menü öğesini seçin.  
  
    3. **Tüm kullanıcılardan Işlem göster** onay kutusunu seçin.  
  
    4. Hata ayıklamak için konak çalışan işlemi W3wp.exe seçin (Windows XP 'de ASPNet_wp.exe ' i seçin).  
  
3. Artık hizmet kodunda kesme noktaları ayarlayabilir ve özel durumlarda kesme noktalarını etkinleştirebilirsiniz.  
  
4. İstemci proje öğesine sağ tıklayın ve **Hata Ayıkla**, **Yeni örnek Başlat**' ı seçin.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Hizmet IIS 'de güvenlik amacıyla barındırılıyorsa, örnekleri ile işiniz bittiğinde, kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Örnekleri Oluşturma](building-the-samples.md)
- [WCF örnekleri için sorun giderme Ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
