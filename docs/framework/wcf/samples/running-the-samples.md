---
title: Windows Communication Foundation Örneklerini Çalıştırma
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: df984f2464084948cdaa51dab96554de9400911f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965493"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örneklerini Çalıştırma
Windows Communication Foundation (WCF) örnekleri, tek makineli veya bir çapraz makine yapılandırmasında çalıştırılabilir. Sağlandığı gibi, örnekler tek bir makinede çalıştırılmaya hazırlardır. Bir çapraz makine yapılandırmasında, bir örneğin yapılandırma dosyası ayarlarını değiştirmek gereklidir. Aşağıdaki yordamlarda, aynı makine ve makineler arası yapılandırmalarda bir örneği çalıştırmanın açıklanmaktadır. Internet Information Services (IIS) ve şirket içinde barındırılan örneklerde barındırılan hizmetler için adımlarda Çeşitlemeler bulunduğunu unutmayın. Çoğu örnek IIS 'de barındırılır; nasıl barındırıldığını öğrenmek için örnek Benioku bilgilerine bakın.  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], IIS 'de barındırılmayan örnekler, http. sys ile bir dinleyici kaydetmek için yükseltilmiş ayrıcalıklar gerektirir. Hizmetin dinlediği hesapla hizmetin dinleme adreslerini kaydetmek için Httpcfg. exe ' yi kullanın veya hizmeti yönetici ayrıcalıklarıyla çalışan bir komut isteminden çalıştırın.  
  
> [!NOTE]
> WCF örneklerinden herhangi birini oluşturmadan veya çalıştırmadan önce, [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Hizmet IIS tarafından barındırılıyorsa, şu adresi girerek hizmete bir tarayıcı kullanarak erişebildiğinizden emin olun: `http://localhost/servicemodelsamples/service.svc`. Yanıt olarak bir onay sayfası görüntülenmelidir. Onay sayfası görüntülenmiyorsa, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
2. Hizmet şirket içinde barındırılıyorsa, \ service\bin ' den Service. exe ' yi dile özgü klasörün altında çalıştırın. Hizmet etkinliği, hizmet konsolu penceresinde görüntülenir.  
  
3. \ Client\bin\\' den dile özgü klasörden Client. exe ' yi çalıştırın. İstemci etkinliği istemci konsol penceresinde görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Hizmet IIS 'de barındırılıyorsa:  
  
    1. Hizmet makinesinde, ServiceModelSamples adlı bir sanal dizin oluşturun. [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) bulunan Setupvroot. bat toplu iş dosyası, disk dizini ve sanal dizin oluşturmak için kullanılabilir.  
  
    2. Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki ServiceModelSamples sanal dizinine kopyalayın. Dosyalarını \Bin dizinine dahil ettiğinizden emin olun.  
  
    3. Bir tarayıcı kullanarak hizmete istemci makineden erişebilme sınamasını yapın.  
  
     Hizmet kendi kendine barındırılıyorsa:  
  
    1. Hizmet makinesinde, hizmet dosyalarını tutacak bir dizin oluşturun.  
  
    2. Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet makinesine kopyalayın.  
  
    3. Hizmet yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
    4. Komut isteminden Service. exe ' yi başlatın.  
  
2. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.  
  
3. Uç nokta adresini ayarlayın.  
  
    1. Hizmet bir etki alanı hesabı altında çalışmıyorsa, istemci yapılandırma dosyasını açın ve uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
    2. Hizmet bir etki alanı hesabı altında çalışıyorsa, hizmete karşı Svcutil. exe dosyasını çalıştırarak istemci yapılandırmasını yeniden oluşturun. Svcutil. exe ' yi çalıştırma hakkında daha fazla bilgi için bkz. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md). Örnekteki yapılandırma dosyası yerine oluşturulan dosyayı kullanın. Oluşturulan yapılandırma dosyasında ek kimlik bilgileri bulunur ve varsayılan ayarlar olsalar bile hizmet uç noktasına bağlanmak için gerekli tüm ayarları içerir. Kimlik bilgileri hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)ve [ \<kimlik >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4. İstemci makinesinde, bir komut isteminden Client. exe ' yi başlatın.  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1. **Build** menüsünü veya CTRL + SHIFT + B kullanarak çözümü (hem istemci hem de hizmet) oluşturun.  
  
2. Hizmet IIS 'de barındırılıyorsa:  
  
    1. Adresi `http://localhost/servicemodelsamples/service.svc`girerek bir tarayıcı kullanarak hizmeti etkinleştirin.  
  
    2. Çözümde **Hata Ayıkla** menüsünü ve **İşleme İliştir** menü öğesini seçin.  
  
    3. **Tüm kullanıcılardan Işlem göster** onay kutusunu seçin.  
  
    4. Hata ayıklamak için W3wp. exe konak çalışan işlemini seçin (Windows XP 'de ASPNet_wp. exe ' yi seçin).  
  
3. Artık hizmet kodunda kesme noktaları ayarlayabilir ve özel durumlarda kesme noktalarını etkinleştirebilirsiniz.  
  
4. İstemci proje öğesine sağ tıklayın ve **Hata Ayıkla**, **Yeni örnek Başlat**' ı seçin.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Hizmet IIS 'de güvenlik amacıyla barındırılıyorsa, örnekleri ile işiniz bittiğinde, kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Örnekleri Derleme](../../../../docs/framework/wcf/samples/building-the-samples.md)
- [WCF örnekleri için sorun giderme Ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
