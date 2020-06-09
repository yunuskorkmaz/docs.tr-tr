---
title: Windows Communication Foundation Örnekleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 53599b3b1827651b48df9921bb59a679a36ee39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592625"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örnekleri Oluşturma

Windows Communication Foundation (WCF) örnekleri, Visual Studio IDE kullanılarak veya komut satırından **MSBuild** komutu kullanılarak oluşturulabilir. Her iki yordam de bu konuda açıklanmaktadır.

> [!NOTE]
> WCF örneklerinden herhangi birini oluşturmadan veya çalıştırmadan önce, [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

## <a name="to-build-the-sample-using-a-command-prompt"></a>Komut istemi kullanarak örneği oluşturmak için

1. Visual Studio için Geliştirici Komut İstemi açın ve örneği yüklediğiniz dizin konumunun altındaki dile özgü alt dizine gidin.

2. `msbuild`Komut satırına yazın. İstemci program dosyaları *client\bin* 'e kurulmuştur ve hizmet programı dosyaları *service\bin*'e yerleştirilmiştir. Hizmet Internet Information Services (IIS) tarafından barındırılıyorsa, hizmet programı dosyaları da *servicemodelsamples* dizinine ve *\Bin* alt dizinine kopyalanır.

> [!NOTE]
> Üzerinde çalışan hesap için değiştirme izinleri vermek üzere *%systemdrive%\ınetpub\wwwroot* üzerinde ACL 'ler ayarlamanız gerekir. Aksi takdirde, bazı derleme sonrası olaylar başarısız olur. Alternatif olarak, ACL 'Leri olduğu gibi bırakabilir ve yönetici olarak SDK komut istemi 'ni çalıştırabilirsiniz.

## <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için

1. Visual Studio 'daki **Dosya** menüsünde **Open**  >  **Proje/çözüm**aç ' ı seçin. Örneği yüklediğiniz dizinin altındaki dile özgü alt dizine gidin ve Visual Studio 'da çözümü açmak için. sln dosya simgesine çift tıklayın.

1. **Derle** menüsünde **çözümü yeniden derle**' yi seçin.

   İstemci program dosyaları, client\bin 'e kurulmuştur ve hizmet programı dosyaları service\bin. için oluşturulmuştur Hizmet IIS 'de barındırılıyorsa, hizmet programı dosyaları da *servicemodelsamples* dizinine ve *\Bin* alt dizinine kopyalanır.

> [!NOTE]
> Üzerinde çalışan hesap için değiştirme izinleri vermek üzere%systemdrive%\ınetpub\wwwroot üzerinde ACL 'Ler ayarlamanız gerekir. Aksi takdirde, bazı derleme sonrası olaylar başarısız olur. Alternatif olarak, ACL 'Leri olduğu gibi bırakabilir ve SDK komut istemi 'ni veya Visual Studio 'Yu yönetici olarak çalıştırabilirsiniz. Bazı Visual Studio eylemleri (örneğin, ASP.Net Worker işlemine bir hata ayıklayıcı eklemek) ayrıca yönetim ayrıcalıkları gerektirir.

## <a name="setup-batch-files-and-scripts"></a>Toplu Iş dosyalarını ve betikleri ayarla
 Setup. exe ve Cleanup. exe toplu iş dosyaları ve betikleri Visual Studio için Geliştirici Komut İstemi çalıştırılmalıdır. Çeşitli dosyaları ayarlama ve Temizleme, yönetici ayrıcalıkları gerektiren görevleri gerçekleştirir ve yönetici ayrıcalıklarıyla başlatılmalıdır.

## <a name="important-security-information-about-metadata-endpoints"></a>Meta veri uç noktaları hakkında önemli güvenlik bilgileri
 Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır. Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil. exe gibi) kullanamazsınız. Örnekleri daha kolay hale getirmek için neredeyse tüm örnekler güvenli olmayan bir meta veri yayımlama uç noktasını kullanıma sunar. Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir. Hizmet meta verilerini yayımlama hakkında daha fazla bilgi için bkz. [meta veri yayımlama davranışı](metadata-publishing-behavior.md) örneği. Meta veri uç noktasının güvenliğini sağlamaya yönelik bir örnek için [özel güvenli meta veri uç noktası](custom-secure-metadata-endpoint.md) örneğine bakın.

## <a name="exception-handling"></a>Özel Durum İşleme
 Genellikle bu örneklere konuşarak, kodu örnek konusuna odaklanmış tutmak için özel durum işleme dahil değildir. Özel durum işleme hakkında daha fazla bilgi için [Beklenen özel durumlar](expected-exceptions.md) örneğine bakın.

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Svcutil ile Istemcileri ve yapılandırmayı yeniden oluşturma
 Çoğu örnek için istemci kodu ve yapılandırmasını yeniden oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz. Bazı örneklerin el ile düzenlenmiş yapılandırması gerekir. Örneğin, istemci sertifikası kimlik bilgilerini kullanan bir örnek için yapılandırmayı yeniden oluşturmak üzere Svcutil. exe ' yi kullanırsanız, önceden yapılandırılmış kimlik bilgilerini el ile belirtmeniz gerekir. Bazı örnekler, oluşturulan kodu etkilemek için belirli Svcutil. exe seçeneklerini kullanır, bu seçenekler belirli örnek konularda belirtilmiştir.

### <a name="to-regenerate-the-client-and-configuration-files"></a>İstemci ve yapılandırma dosyalarını yeniden oluşturmak için

1. Bir SDK komut istemi açın ve örneği yüklediğiniz dizin konumunun altındaki dile özgü alt dizine gidin.

2. Hizmet Web 'de barındırılan bir tür ise aşağıdaki komutu kullanın.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Hizmet şirket içinde barındırılan bir tür ise aşağıdaki komutu yazın.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     `http://localhost:8000/ServiceModelSamples/service.svc/mex`Şirket içinde barındırılan Hizmetin MEX uç noktasının adresiyle değiştirin.

     İstemciyi Visual Basic bir türde oluşturmak için aşağıdaki komutu kullanın.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Hizmet kendi kendine barındırılan bir tür ise aşağıdaki komutu kullanın.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > İstemci yapılandırması oluşturulmasını atlamak için **/noconfig** seçeneğini ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Örneklerini Çalıştırma](running-the-samples.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
