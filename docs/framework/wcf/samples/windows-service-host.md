---
title: Windows Hizmet Konağı
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143531"
---
# <a name="windows-service-host"></a>Windows Hizmet Konağı
Bu örnek, yönetilen bir Windows Hizmetinde barındırılan bir Windows Communication Foundation (WCF) hizmetini gösterir. Windows Hizmetleri **Denetim Masası'ndaki** Hizmetler applet kullanılarak denetlenir ve sistem yeniden başlatıldıktan sonra otomatik olarak başlatılacak şekilde yapılandırılabilir. Örnek bir istemci programı ve bir Windows Service programından oluşur. Hizmet bir .exe programı olarak uygulanır ve kendi barındırma kodunu içerir. Windows İşlem etkinleştirme Hizmetleri (WAS) veya Internet Information Services (IIS) gibi diğer barındırma ortamlarında barındırma kodu yazmanız gerekmez.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Bu hizmeti yaptıktan sonra, diğer Windows Hizmetleri gibi Installutil.exe yardımcı programı ile yüklenmesi gerekir. Hizmette değişiklik yapacaksanız, önce `installutil /u`'yi kaldırın. Bu örnekte yer alan Setup.bat ve Cleanup.bat dosyaları, Windows Hizmeti'ni yüklemek ve başlatmak ve Windows Hizmeti'ni kapatıp kaldırmak için verilen komutlardır. WCF hizmeti istemcilere yalnızca Windows Hizmeti çalışıyorsa yanıt verebilir. Windows Hizmeti'ni **Denetim Masası'ndaki** Hizmetler uygulamasını kullanarak durdurur <xref:System.ServiceModel.EndpointNotFoundException> ve istemciyi çalıştırırsanız, istemci hizmete erişmeye çalıştığında bir özel durum oluşur. Windows Hizmeti'ni yeniden başlatıp istemciyi yeniden çalıştırın, iletişim başarılı olur.  
  
 Hizmet kodu bir yükleyici sınıfı, ICalculator sözleşmesini uygulayan bir WCF hizmet uygulama sınıfı ve çalışma zamanı ana bilgisayar olarak çalışan bir Windows Service sınıfı içerir. Devralan yükleyici <xref:System.Configuration.Install.Installer>sınıfı, installutil.exe aracı tarafından programın NT hizmeti olarak yüklenmesini sağlar. Hizmet uygulama sınıfı, `WcfCalculatorService`temel bir hizmet sözleşmesi uygulayan bir WCF hizmetidir. Bu WCF hizmeti, Windows Service `WindowsCalculatorService`sınıfının içinde barındırılır. Windows Hizmeti olarak nitelendirmek için, <xref:System.ServiceProcess.ServiceBase> sınıf devralır <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> <xref:System.ServiceProcess.ServiceBase.OnStop> ve ve yöntemleri uygular. In <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> `WcfCalculatorService` bir nesne türü için oluşturulur ve açıldı. Içinde, <xref:System.ServiceProcess.ServiceBase.OnStop>ServiceHost <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> <xref:System.ServiceModel.ServiceHost> nesnenin yöntemini çağırarak kapatılır. Ana bilgisayar temel adresi, [ \<hizmet>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesinin bir çocuğu olan [ \<ana bilgisayar>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) öğesinin bir çocuğu olan [ \<baseAddresses>'nin ](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)bir alt öğesi olan [ \<>ekle](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) öğesi kullanılarak yapılandırılır.  
  
 Tanımlanan bitiş noktası temel adresi ve [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanır. Aşağıdaki örnek, temel adresin yapılandırmasını ve Hesap Makinesi Hizmetini ortaya çıkaran bitiş noktasını gösterir.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Çözüm yüklendikten sonra, Installutil.exe aracını kullanarak Windows hizmetini yüklemek için yükseltilmiş visual studio 2012 komut isteminden Setup.bat çalıştırın. Hizmet Hizmetleri'nde görünmelidir.  
  
4. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
