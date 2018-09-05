---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1f95356b0b473b297b36c7661c849589e9c0d6ef
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520820"
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası
Bu örnek kullanımını kapsayan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırması merkezi yönetilmesine izin verir. Bu ayrıca yapılandırma seçtikten veya uygulama etki alanı yükleme saatinden sonra değiştirildi senaryolarda yararlı olabilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek nasıl kullanılacağını gösterir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> varsayılan uygulama yapılandırma dosyası kullanmak zorunda kalmadan bir istemci uygulama, belirli bir yapılandırma dosyası eklemek için.  
  
 Örnek, iki projeden oluşan. İlk proje istemcilerden gelen iletilere yanıt vermek için çalışan basit bir hizmettir. İkinci proje iki oluşturan bir istemci uygulamasıdır <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> kullanarak nesneleri bir <xref:System.Configuration.ExeConfigurationFileMap> Test.config yapılandırma dosyası için ve onları hizmetiyle iletişim kurmak için kullanır. Her iki istemcinin Test.config içinde belirtilen yapılandırma kullanılarak hizmetiyle iletişim kurar.  
  
 Aşağıdaki kod, bir istemci uygulaması için özel bir yapılandırma dosyasına ekler.  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  (2 projeler) ConfigurationChannelFactory çözüme sağ tıklayın ve ardından **özellikleri**.  
  
3.  İçinde **ortak özellikler**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.  
  
4.  Taşıma **hizmet** listenin başına proje ile **eylem 'Start'** ve ardından taşıyın **istemci** sonra proje **hizmet**proje ile aynı zamanda **eylem 'Start'**, bu nedenle **istemci** proje sonra yürütülür **hizmet** proje.  
  
5.  Tıklayın **Tamam**ve ardından örneği çalıştırmak için F5'i (veya CTRL + F5) tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
