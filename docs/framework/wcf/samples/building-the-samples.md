---
title: "Windows Communication Foundation Örnekleri Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: "33"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efb45a09fd74d397ceb95fc7e1bad7a0a5f80309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="building-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örnekleri Derleme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Örnekleri, Visual Studio 2010 veya kullanarak oluşturulabilen **msbuild** komut satırından komutu. Bu konuda iki yordam açıklanmaktadır.  
  
> [!NOTE]
>  Derleme veya herhangi birini çalıştıran önce [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri, olun gerçekleştirilen [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>Bir komut istemi kullanarak örneği oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla ve örnek yüklendiği dizin konumu altında dile özgü alt dizine gidin.  
  
2.  Tür `msbuild` komut satırında. İstemci program dosyaları için client\bin yerleşiktir ve hizmet program dosyaları için service\bin oluşturulur. Internet Information Services (IIS) tarafından barındırılan hizmetindeki, hizmet program dosyaları servicemodelsamples dizin ve \bin alt dizini de kopyalanır.  
  
> [!NOTE]
>  Vermek %systemdrive%\inetpub\wwwroot ACL'leri ayarlamalısınız altında çalışırken hesaba izinleri değiştirin. Aksi takdirde bazı yapı olayları başarısız gönderin. Alternatif olarak, olan ve SDK komut istemini yönetici olarak çalıştır ACL'leri bırakabilirsiniz.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1.  Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2 ve çalışan [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], çalıştırmalısınız [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yükseltilmiş iznine sahip. Bunu yapmak için Başlat menüsünde simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**.  
  
2.  Gelen **dosya** menüde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], tıklatın **açık**, ardından **proje/çözüm**. Dile özgü alt örnek yüklenen dizini altında gidin ve çözümde açmak için .sln dosyasını simgesini çift [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
3.  İçinde **yapı** menüsünde, select **çözümü yeniden derle**. İstemci program dosyaları için client\bin yerleşiktir ve hizmet program dosyaları için service\bin oluşturulur. Hizmet IIS'de barındırılıyorsa, hizmet program dosyalarını servicemodelsamples dizin ve \bin alt dizini de kopyalanır.  
  
> [!NOTE]
>  Vermek %systemdrive%\inetpub\wwwroot ACL'leri ayarlamalısınız altında çalışırken hesaba izinleri değiştirin. Aksi takdirde bazı yapı olayları başarısız gönderin. Alternatif olarak, olan ve SDK komut istemi veya Visual Studio Yönetici olarak çalıştır ACL'leri bırakabilirsiniz. (Bir hata ayıklayıcısı ASP.Net çalışan işlemine iliştirme) gibi bazı Visual Studio eylemleri de yönetici ayrıcalıkları gerektirir.  
  
## <a name="setup-batch-files-and-scripts"></a>Kurulum toplu iş dosyaları ve komut dosyaları  
 Setup.exe ve Cleanup.exe toplu iş dosyaları ve komut dosyaları için bir Visual Studio komut isteminden çalıştırılması gerekir. Yukarı ve dosyaları temizlenmesi birkaç kümesi yönetici ayrıcalıkları gerektiren ve yönetici ayrıcalıklarına sahip başlatılması gereken görevleri gerçekleştirir.  
  
## <a name="important-security-information-about-metadata-endpoints"></a>Meta veri uç noktalarını hakkında önemli güvenlik bilgileri  
 Olası hassas hizmeti meta verileri, için varsayılan yapılandırma, yanlışlıkla açığa çıkmasını önlemek amacıyla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri, meta veri yayımlama devre dışı bırakır. Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe. Daha kolay örnekleriyle denemeler yapmak için güvenli olmayan meta veri yayımlama uç noktası neredeyse tüm örneklerini kullanıma sunar. Bu tür uç noktaları anonim kimlik doğrulamasız tüketicilere potansiyel olarak kullanılabilir ve bakım gibi uç noktaları dağıtmadan önce genel olarak disclosing bir hizmetin meta veri uygun olduğundan emin olmak için izlenmelidir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Hizmet meta veri yayımlama bkz [meta veri yayımlama davranışı](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) örnek. Bkz: [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örnek bir meta veri uç noktası güvenli hale getirme örneği.  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 Genel olarak bakıldığında bu örnekleri özel durum örnek konu üzerinde odaklanmış kod tutmak için işleme dahil etmeyin. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel durum işleme bkz [beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) örnek.  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>İstemcileri ve Svcutil yapılandırmayla yeniden oluşturuluyor  
 Kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci kodu ve yapılandırma örnekleri çoğu için yeniden oluşturmak için. Bazı örnekler el ile düzenlenmiş yapılandırma gerektirmez. Örneğin, istemci sertifikası kimlik bilgilerini kullanan bir örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanma, daha önce yapılandırılan kimlik bilgileri el ile belirtmeniz gerekir. Bazı örnekler, oluşturulan kod etkilemek için belirli Svcutil.exe seçenekleri kullanın, bu seçenekler belirli örnek konularında belirtilmiş.  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>İstemci ve yapılandırma dosyaları yeniden oluşturmak için  
  
1.  SDK komut istemi açın ve örnek yüklendiği dizin konumu altında dile özgü alt gidin.  
  
2.  Hizmetin Web barındırılan bir tür ise, aşağıdaki komutu kullanın.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Hizmet kendi kendini barındıran aşağıdaki komutu yazın.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Http://localhost:8000/ServiceModelSamples/Service.svc/Mex kendini barındıran hizmet mex bitiş noktası adresiyle değiştirin.  
  
     İstemci bir Visual Basic türü oluşturmak için aşağıdaki komutu kullanın.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     Hizmet kendi kendini barındıran bir tür ise, aşağıdaki komutu kullanın.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  Atlamak için istemci yapılandırması nesil eklemek **/noconfig** seçeneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
