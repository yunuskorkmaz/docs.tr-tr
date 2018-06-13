---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: fc3a564128e520133c2404a82438e692b1381875
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806584"
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası
Bu örnek kullanımını kapsayan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırması merkezi yönetilmesine izin verir. Bu ayrıca yapılandırması seçili veya uygulama etki alanı yükleme sonra saati değişti senaryolarda yararlı olabilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek nasıl kullanılacağını göstermektedir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> varsayılan uygulama yapılandırma dosyası kullanmak zorunda kalmadan bir istemci uygulaması için belirli yapılandırma dosyası eklemek için.  
  
 Örnek iki projeden oluşan. İlk proje istemcilerinden gelen iletileri yanıtlamak için çalışan basit bir hizmettir. İki derlemeler bir istemci uygulaması ikinci projedir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> kullanarak nesneleri bir <xref:System.Configuration.ExeConfigurationFileMap> Test.config yapılandırma dosyası için ve bunları hizmetiyle iletişim kurmak için kullanır. Her iki istemcinin Test.config içinde belirtilen yapılandırma kullanılarak hizmetiyle iletişim.  
  
 Aşağıdaki kod, bir istemci uygulaması için özel bir yapılandırma dosyasına ekler.  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  (2 projeleri) ConfigurationChannelFactory çözüme sağ tıklayın ve ardından **özellikleri**.  
  
3.  İçinde **ortak özellikleri**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.  
  
4.  Taşıma **hizmet** ile listenin başına proje **eylemi 'Start'** ve ardından taşıma **istemci** sonra proje **hizmet**projesi de **eylemi 'Start'**, böylece **istemci** proje sonra yürütüldüğünde **hizmet** projesi.  
  
5.  Tıklatın **Tamam**, örneği çalıştırmak için F5'e (veya CTRL + F5'e)'tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
