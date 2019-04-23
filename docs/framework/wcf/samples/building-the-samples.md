---
title: Windows Communication Foundation Örnekleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: b1f1005e32687d2683f757d847d9fa19e098f290
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317863"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örnekleri Oluşturma

Windows Communication Foundation (WCF) örnekleri veya Visual Studio IDE kullanarak oluşturulabilir **msbuild** komut satırından komutu. Bu konudaki her iki yordam açıklanmaktadır.

> [!NOTE]
> Oluşturma veya WCF örnekleri birini çalıştırmadan önce gerçekleştirilen olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>Bir komut istemi kullanarak örneği oluşturmak için

1. Visual Studio için geliştirici komut istemi açın ve dile özgü alt dizinde örnek yüklediğiniz dizin konumuna gidin.

2. Tür `msbuild` komut satırına. İstemci program dosyaları için oluşturulmuş *client\bin* ve hizmet program dosyaları için oluşturulmuş *service\bin*. Internet Information Services (IIS) tarafından barındırılan hizmet, hizmet program dosyaları da kopyalanır *servicemodelsamples* dizin ve kendi *\bin* alt.

> [!NOTE]
> ACL'ler ayarlamalısınız *%systemdrive%\inetpub\wwwroot* vermek için altında çalıştırdığınız hesabına izinleri değiştirin. Aksi halde bazı derleme olayları başarısız gönderin. Alternatif olarak, bunlar ve SDK komut istemini yönetici olarak çalıştır olarak ACL'leri bırakabilirsiniz.

## <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için

1. Gelen **dosya** Visual Studio'da seçim menüsünde **açık** > **proje/çözüm**. Örnek yüklendiği dizinin altında dile özgü alt dizinine gidin ve Visual Studio'da Çözüm açmak için bir .sln dosya simgesini çift tıklatın.

1. Gelen **derleme** menüsünde **çözümü yeniden derle**.

   İstemci program dosyaları için client\bin oluşturulur ve hizmet program dosyaları için service\bin oluşturulur. Hizmet IIS'de barındırılıyorsa, hizmet program dosyaları için de kopyalanır *servicemodelsamples* dizin ve kendi *\bin* alt.

> [!NOTE]
> Vermek %systemdrive%\inetpub\wwwroot ACL'leri ayarlamalısınız altında çalıştırdığınız hesabına izinleri değiştirin. Aksi halde bazı derleme olayları başarısız gönderin. Alternatif olarak, bunlar ve SDK komut istemi veya Visual Studio'yu yönetici olarak çalıştır olarak ACL'leri bırakabilirsiniz. Bazı Visual Studio Eylemler (örneğin, bir hata ayıklayıcı ASP.Net işçi işlemine iliştirme), ayrıca yönetim ayrıcalıkları gerektirir.

## <a name="setup-batch-files-and-scripts"></a>Kurulum toplu iş dosyaları ve betikler
 Setup.exe ve Cleanup.exe toplu iş dosyaları ve betikler, Visual Studio için geliştirici komut isteminden çalıştırmanız gerekir. Birkaç kümesi ayarlama ve temizleme dosyaları yönetim ayrıcalıklarına sahip olmanız ve yönetici ayrıcalıklarına sahip başlatılması gereken görevleri gerçekleştirin.

## <a name="important-security-information-about-metadata-endpoints"></a>Meta veri uç noktalarını hakkında önemli güvenlik bilgileri
 Olası hassas hizmet meta verilerinin yanlışlıkla açığa çıkmasını önlemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı bırakır. Bu varsayılan olarak güvenli, davranıştır ancak ayrıca Aracı (Svcutil.exe gibi) yapılandırmasında hizmetin meta veri yayımlama davranışı açıkça etkinleştirilmediği hizmeti çağırmak için gereken istemci kodu oluşturmak için içeri bir meta veri kullanamayacağı anlamına gelir. Daha kolay örnekleri ile denemeler yapmak için bir güvenli olmayan meta veri yayımlama uç nokta hemen hemen tüm örnekleri kullanıma sunar. Bu uç noktaları için anonim kimlik doğrulamasız tüketiciler potansiyel olarak kullanılabilir ve bu uç noktaları dağıtmadan önce herkese açık şekilde öğrendiği bir hizmet meta verileri uygun olmasına özen gerekir. Hizmet meta verileri yayımlama hakkında daha fazla bilgi için bkz: [meta veri yayımlama davranışı](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) örnek. Bkz: [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örnek meta veri uç noktası güvenli hale getirme örneği.

## <a name="exception-handling"></a>Özel Durum İşleme
 Genel olarak bakıldığında bu örnekleri, örnek konu üzerinde odaklanmış kod saklamak için özel durum işleme içermez. Özel durum işleme hakkında daha fazla bilgi için bkz. [beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) örnek.

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>İstemcileri ve Svcutil yapılandırmayla yeniden oluşturuluyor
 Kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci kodu ve örnekleri çoğu yapılandırması yeniden oluşturmak. Bazı örnekler el ile düzenlenmiş yapılandırma gerektirir. Örneğin, istemci sertifikası kimlik bilgilerini kullanan bir örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, daha önce yapılandırılmış kimlik bilgilerini el ile belirtmeniz gerekir. Bazı örnekler, oluşturulan kod etkilemek için belirli Svcutil.exe seçenekleri kullanın, bu seçenekler belirli örnek konularındaki belirtilir.

### <a name="to-regenerate-the-client-and-configuration-files"></a>İstemci ve yapılandırma dosyalarını yeniden oluşturmak için

1. Bir SDK komut istemi açın ve dile özgü alt dizinde örnek yüklediğiniz dizin konumuna gidin.

2. Hizmetin Web barındırılan bir tür ise, aşağıdaki komutu kullanın.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Hizmet, şirket içinde barındırılan aşağıdaki komutu yazın.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Değiştirin `http://localhost:8000/ServiceModelSamples/service.svc/mex` şirket içinde barındırılan hizmetin mex uç nokta adresi.

     İstemci bir Visual Basic türü oluşturmak için aşağıdaki komutu kullanın.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Hizmet, şirket içinde barındırılan bir tür ise, aşağıdaki komutu kullanın.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Atlamak için istemci yapılandırması nesil ekleme **/noconfig** seçeneği.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Örneklerini Çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
