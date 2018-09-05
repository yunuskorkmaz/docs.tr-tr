---
title: Windows Hizmet Konağı
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 0283fd8b3fd275be9787bb75763e9395091426a3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513677"
---
# <a name="windows-service-host"></a>Windows Hizmet Konağı
Bu örnek, yönetilen bir Windows hizmetinde barındırılan Windows Communication Foundation (WCF) hizmet gösterir. Windows Hizmetleri içindeki Hizmetler uygulamasını kullanarak denetlenir **Denetim Masası** ve sonra sistemi yeniden başlatma otomatik olarak başlatılmasını yapılandırılabilir. Örnek, bir istemci programı ve bir Windows hizmet programı oluşur. Hizmet bir .exe programı olarak uygulanır ve kendi barındırma kodunu içerir. Windows İşlem Etkinleştirme Hizmetleri (WAS) veya Internet Information Services (IIS) gibi diğer barındırma ortamlarında yazmak için gerekli değildir kod barındırma.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Bu hizmeti derledikten sonra Installutil.exe yardımcı programıyla gibi herhangi bir Windows hizmeti yüklü olmalıdır. Hizmete değişiklik yapmak için kullanacaksanız, kendisiyle kaldırmalısınız `installutil /u`. Bu örnekte bulunan Setup.bat ve Cleanup.bat dosyaları yüklemek ve Windows hizmeti'kurmak, başlatmak için ve kapatmak ve Windows hizmetini kaldırmak için komutlardır. Windows Hizmeti çalışıyorsa WCF hizmeti yalnızca istemcilere yanıt verebilir. Gelen hizmetler uygulamasını kullanarak Windows hizmetini durdurun, **Denetim Masası** ve istemcisini çalıştıran bir <xref:System.ServiceModel.EndpointNotFoundException> istemci hizmeti erişmeye çalışırken özel durum oluşur. Windows hizmetini yeniden başlatın ve istemciyi yeniden çalıştırın, iletişim başarılı olur.  
  
 Hizmet kodunu bir yükleyici sınıfı ICalculator sözleşme uygulayan bir WCF hizmeti uygulaması sınıf ve çalışma zamanı ana bilgisayarı olarak davranan bir Windows hizmet sınıfı içerir. Devralınan Yükleyici sınıfı <xref:System.Configuration.Install.Installer>, Installutil.exe aracı tarafından bir NT hizmeti olarak yüklenecek program sağlar. Hizmet uygulaması sınıfı `WcfCalculatorService`, temel hizmet sözleşmesini uygulayan bir WCF hizmeti. Bu WCF hizmeti olarak adlandırılan bir Windows hizmeti sınıf içinde barındırıldığı `WindowsCalculatorService`. Bir Windows hizmeti olarak nitelemek için sınıf devraldığı <xref:System.ServiceProcess.ServiceBase> ve uygulayan <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> ve <xref:System.ServiceProcess.ServiceBase.OnStop> yöntemleri. İçinde <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> nesne için oluşturulan `WcfCalculatorService` yazın ve açılır. İçinde <xref:System.ServiceProcess.ServiceBase.OnStop>, çağırarak ServiceHost kapalı <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> yöntemi <xref:System.ServiceModel.ServiceHost> nesne. Ana bilgisayarın temel adres kullanılarak yapılandırılır [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) bir alt öğesi, [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), bir alt öğesi olan [ \<konak >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) bir alt öğesi olan [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesi.  
  
 Tanımlanan bir uç nokta temel adresi kullanır ve [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Aşağıdaki örnek, taban adresini ve bunun yanı sıra CalculatorService kullanıma sunduğu uç nokta yapılandırmasını gösterir.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Çözüm oluşturulduktan sonra yükseltilmiş Setup.bat çalıştırma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Installutil.exe Aracı'nı kullanarak Windows hizmetini yüklemek için komut istemi. Hizmet hizmetlerinde görüntülenmelidir.  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
