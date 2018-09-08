---
title: Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: e016dffdaf93b222c1fd2380bfa175256b009068
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188312"
---
# <a name="configuration-based-activation"></a>Yapılandırma Temelli Etkinleştirme
Bu örnek, bir .svc dosya gerek kalmadan Windows Communication Foundation (WCF) hizmetlerini etkinleştirme gösterir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte istemci WCF test istemcisi ve IIS'de barındırılan hizmet.  
  
> [!NOTE]
>  Bu örnek için Kurulum ve yapılandırma yönergeleri Bu konunun sonunda yer alır.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>.Svc dosya gerektirmeden hizmetlerin etkinleştirme  
 İçinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], bir hizmeti etkinleştirme için gerekli .svc dosyasıdır. Ek dosya dağıtılması ve uygulama ile birlikte korunur için gerekli olduğu için bu ek yönetim yükünü neden oldu. Sürümüyle [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], etkinleştirme bileşenlerini, uygulama yapılandırma dosyası kullanılarak yapılandırılabilir.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] Yeni bir yapılandırma öğesi sunar (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> uygulama yapılandırma dosyası. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Koleksiyonu aşağıdaki kod örneğinde gösterildiği gibi hizmetleri etkinleştirmek için koleksiyonu kabul eder.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Yapılandırma .svc dosyalarını yapılandırmanız için çok benzer görünür hale getirmek için gözlem olur. Sunulan ek bir özniteliktir `relativeAddress` hizmetinin adresini sağlar. Hizmetin göreli adresini de hizmet için sanal yolu var. Dosyadan Web.config dosyasına ana bilgisayar alır `virtualPath` konumu, konak değişkenidir; Aksi takdirde, üst klasörü yinelemeli olarak arar.  
  
> [!NOTE]
>  Bu örnek, IIS'de işleve barındırma gerektirir.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Service.csproj dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Hizmet WCFTestClient.exe çalıştırarak test edin.  
  
4.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE klasöre gidin.  
  
5.  WcfTestClient.exe çalıştırın.  
  
6.  MEX adresa hizmetinin ayarlayın.  
  
7.  Hizmet adresinin ayarlamak için CTRL + SHIFT + A tuşlarına basın.  
  
8.  Adresini http://localhost/ServiceModelSamples/Calculator.svc.  
  
9. Gerçekleştirmek `Add` işlemi. Değer kümesi üzerinde `n1` parametresini 10 ve ayarlanan değere `n2` 15 parametresi.  
  
10. Tuşuna **çağırma**.  
  
     Beklenen sonuç 25'tir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  IIS ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırma sonra çözümü oluşturuldu. ServiceModelSamples dizin artık IIS uygulaması olarak görünmelidir.  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
