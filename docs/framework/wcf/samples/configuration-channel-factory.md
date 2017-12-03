---
title: "Yapılandırma Kanal Fabrikası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa0f4aec0a673a07c6b6d752d8609caedbcfa4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası
Bu örnek kullanımını kapsayan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Merkezi Yönetimi sağlayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci yapılandırması. Bu ayrıca yapılandırması seçili veya uygulama etki alanı yükleme sonra saati değişti senaryolarda yararlı olabilir.  
  
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
  
4.  Taşıma **hizmet** ile listenin başına proje **eylemi 'Start'**ve ardından taşıma **istemci** sonra proje **hizmet**projesi de **eylemi 'Start'**, böylece **istemci** proje sonra yürütüldüğünde **hizmet** projesi.  
  
5.  Tıklatın **Tamam**, örneği çalıştırmak için F5'e (veya CTRL + F5'e)'tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
