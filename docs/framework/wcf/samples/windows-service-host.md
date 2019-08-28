---
title: Windows Hizmet Konağı
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 2f2024a984111a826adab31ca15f1a46f9733de5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045401"
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Bu hizmeti oluşturduktan sonra, diğer tüm Windows Hizmetleri gibi InstallUtil. exe yardımcı programıyla birlikte yüklenmelidir. Hizmette değişiklik yapacaksanız, önce bunu ile `installutil /u`kaldırmanız gerekir. Bu örneğe eklenen Setup. bat ve Cleanup. bat dosyaları, Windows hizmetini yükleme ve başlatma ve Windows hizmetini kapatma ve kaldırma komutlardır. WCF hizmeti yalnızca Windows hizmeti çalışıyorsa istemcilere yanıt verebilir. Windows hizmetini **Denetim Masası** 'ndan hizmetler uygulamasını kullanarak durdurur ve istemcisini çalıştırırsanız, istemci hizmete erişmeye çalıştığında bir <xref:System.ServiceModel.EndpointNotFoundException> özel durum oluşur. Windows hizmetini yeniden başlatıp istemciyi yeniden çalıştırırsanız, iletişim başarılı olur.  
  
 Hizmet kodu, bir yükleyici sınıfı, Icalrealtor sözleşmesini uygulayan bir WCF hizmeti uygulama sınıfı ve çalışma zamanı ana bilgisayarı görevi gören bir Windows hizmeti sınıfı içerir. Öğesinden <xref:System.Configuration.Install.Installer>devralan Yükleyici sınıfı, programın InstallUtil. exe aracı tarafından bir NT hizmeti olarak yüklenmesine izin verir. Hizmet uygulama sınıfı `WcfCalculatorService`, temel bir hizmet sözleşmesini uygulayan bir WCF hizmetidir. Bu WCF hizmeti adlı `WindowsCalculatorService`bir Windows hizmeti sınıfı içinde barındırılır. Bir Windows hizmeti olarak nitelendirmek için, sınıfı öğesinden <xref:System.ServiceProcess.ServiceBase> devralır ve <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> ve <xref:System.ServiceProcess.ServiceBase.OnStop> yöntemlerini uygular. ' <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>De, <xref:System.ServiceModel.ServiceHost> `WcfCalculatorService` türü için bir nesne oluşturulur ve açılır. İçinde <xref:System.ServiceProcess.ServiceBase.OnStop>ServiceHost, <xref:System.ServiceModel.ServiceHost> nesnesinin <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> yöntemi çağırarak kapalıdır. Konağın temel adresi [, \<ana bilgisayar >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) öğesinin [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md) [bir altöğesiolan>BaseAddressöğesininbiraltöğesiolanAdd>öğesikullanılarakyapılandırılır.\<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesi.  
  
 Tanımlanan uç nokta, temel adresi ve bir [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanır. Aşağıdaki örnek, temel adresin yapılandırmasını ve Hesaplatorservice 'i kullanıma sunan uç noktayı gösterir.  
  
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

- [AppFabric barındırma ve kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
