---
title: "Yapılandırma Temelli Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db67447ce262949c9ad302a37420fc7023264bd2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-based-activation"></a>Yapılandırma Temelli Etkinleştirme
Bu örnek nasıl etkinleştirileceği gösteren [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] .svc dosya gerektirmeden Hizmetleri.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, istemcidir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemcisi ve hizmeti IIS içinde barındırılır.  
  
> [!NOTE]
>  Kurulum ve yapılandırma yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>.Svc dosya gerektirmeden hizmetlerin etkinleştirme  
 İçinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], .svc dosyasındaki bir hizmeti etkinleştirmek için gerekli. Ek dosya dağıtılması ve uygulamayı ile birlikte saklanır için gerekli olduğu için bu ek yönetim yükünü neden oldu. Sürümü ile [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], etkinleştirme bileşenleri uygulama yapılandırma dosyası kullanılarak yapılandırılabilir.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]Yeni bir yapılandırma öğesi sunar (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> uygulama yapılandırma dosyasının. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Koleksiyonu aşağıdaki kod örneğinde gösterildiği gibi etkinleştirmek için hizmetler koleksiyonu kabul eder.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Yapmak için gözlem yapılandırma .svc dosyalarını yapılandırma için çok benzer görünüyor. Eklenen ek bir özniteliktir `relativeAddress` hizmetinin adresini sağlar. Göreli Ayrıca hizmet için sanal yolu adresidir. Dosyadan Web.config dosyası ana bilgisayarı alır `virtualPath` konumu, ana bilgisayar, yoksa kendi üst klasörü özyinelemeli olarak arar.  
  
> [!NOTE]
>  Bu örnek, IIS'de işleve barındırma gerektirir.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Service.csproj dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Hizmet WCFTestClient.exe çalıştırarak sınayın.  
  
4.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE klasöre gidin.  
  
5.  WcfTestClient.exe çalıştırın.  
  
6.  Hizmetinin MEX adresi ayarlayın.  
  
7.  Hizmet adresini ayarlamak için CTRL + SHIFT + A basın.  
  
8.  Adres için http://localhost/ServiceModelSamples/Calculator.svc ayarlayın.  
  
9. Gerçekleştirmek `Add` işlemi. Değeri ayarlayın `n1` 10 ve ayarlanmış değeri parametresi `n2` 15 parametresi.  
  
10. Tuşuna **çağırma**.  
  
     Beklenen sonucu 25'tir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  IIS ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırmak sonra çözüm oluşturulmadı. ServiceModelSamples dizini artık bir IIS uygulaması olarak görünmelidir.  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
