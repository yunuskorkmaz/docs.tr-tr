---
title: Windows Hizmet Konağı
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: ab1effe93a1572f5d4ce5296bba99dad24f9cbca
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094793"
---
# <a name="windows-service-host"></a>Windows Hizmet Konağı
Bu örnek, yönetilen bir Windows hizmetinde barındırılan bir Windows Communication Foundation (WCF) hizmetini gösterir. Windows Hizmetleri **Denetim Masası** 'ndaki Hizmetler uygulaması kullanılarak denetlenir ve sistem yeniden başlatıldıktan sonra otomatik olarak başlayacak şekilde yapılandırılabilir. Örnek, bir istemci programından ve bir Windows hizmeti programından oluşur. Hizmet bir. exe programı olarak uygulanır ve kendi barındırma kodunu içerir. Windows Işlem etkinleştirme Hizmetleri (WAS) veya Internet Information Services (IIS) gibi diğer barındırma ortamlarında, barındırma kodu yazmanız gerekmez.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Bu hizmeti oluşturduktan sonra, diğer tüm Windows Hizmetleri gibi InstallUtil. exe yardımcı programıyla birlikte yüklenmelidir. Hizmette değişiklik yapacaksanız öncelikle `installutil /u`ile kaldırmanız gerekir. Bu örneğe eklenen Setup. bat ve Cleanup. bat dosyaları, Windows hizmetini yükleme ve başlatma ve Windows hizmetini kapatma ve kaldırma komutlardır. WCF hizmeti yalnızca Windows hizmeti çalışıyorsa istemcilere yanıt verebilir. Windows hizmetini **Denetim Masası** 'ndan hizmetler uygulamasını kullanarak durdurur ve istemcisini çalıştırırsanız, istemci hizmete erişmeye çalıştığında <xref:System.ServiceModel.EndpointNotFoundException> bir özel durum oluşur. Windows hizmetini yeniden başlatıp istemciyi yeniden çalıştırırsanız, iletişim başarılı olur.  
  
 Hizmet kodu, bir yükleyici sınıfı, Icalrealtor sözleşmesini uygulayan bir WCF hizmeti uygulama sınıfı ve çalışma zamanı ana bilgisayarı görevi gören bir Windows hizmeti sınıfı içerir. <xref:System.Configuration.Install.Installer>devralan Yükleyici sınıfı, programın InstallUtil. exe aracı tarafından bir NT hizmeti olarak yüklenmesine izin verir. `WcfCalculatorService`hizmet uygulama sınıfı, temel bir hizmet sözleşmesini uygulayan bir WCF hizmetidir. Bu WCF hizmeti `WindowsCalculatorService`adlı bir Windows hizmeti sınıfı içinde barındırılır. Bir Windows hizmeti olarak nitelendirmek için, sınıf <xref:System.ServiceProcess.ServiceBase> devralır ve <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> ve <xref:System.ServiceProcess.ServiceBase.OnStop> yöntemlerini uygular. <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, `WcfCalculatorService` türü için <xref:System.ServiceModel.ServiceHost> bir nesne oluşturulur ve açılır. <xref:System.ServiceProcess.ServiceBase.OnStop>, ServiceHost, <xref:System.ServiceModel.ServiceHost> nesnesinin <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> yöntemi çağırarak kapalıdır. Konağın temel adresi,\<[service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesinin bir alt öğesi olan\<[ana bilgisayar >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) öğesinin bir alt öğesi olan [\<BaseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)bir alt öğesi olan [\<Add >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) öğesi kullanılarak yapılandırılır.  
  
 Tanımlanan uç nokta, temel adresi ve [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanır. Aşağıdaki örnek, temel adresin yapılandırmasını ve Hesaplatorservice 'i kullanıma sunan uç noktayı gösterir.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Çözüm derlendikten sonra, InstallUtil. exe aracını kullanarak Windows hizmetini yüklemek için, yükseltilmiş bir Visual Studio 2012 komut isteminden setup. bat dosyasını çalıştırın. Hizmet, hizmetler 'de görünmelidir.  
  
4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
