---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1a236f1812d3124e83702a97e1877b7fec10be64
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715498"
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası
Bu örnek <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>kullanımını ele alır. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>, WCF istemci yapılandırmasının merkezi yönetimine izin verir. Bu Ayrıca, uygulamanın etki alanı yükleme zamanından sonra yapılandırmanın seçildiği veya değiştiği senaryolarda yararlı olabilir.

## <a name="demonstrates"></a>Gösterir
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Tartışma
 Bu örnek, varsayılan uygulama yapılandırma dosyasını kullanmak zorunda kalmadan, belirli bir yapılandırma dosyasını bir istemci uygulamasına eklemek için <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> nasıl kullanacağınızı gösterir.

 Örnek iki projeden oluşur. İlk proje, istemcilerden gelen iletileri yanıtlamak için çalışan basit bir hizmettir. İkinci proje, test. config yapılandırma dosyası için bir <xref:System.Configuration.ExeConfigurationFileMap> kullanarak iki <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> nesnesi oluşturan ve hizmet ile iletişim kurmak için bunları kullanan bir istemci uygulamadır. Her iki istemci de test. config dosyasında belirtilen yapılandırmayı kullanarak hizmetle iletişim kurar.

 Aşağıdaki kod, bir istemci uygulamasına özel bir yapılandırma dosyası ekler.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Yönetici ayrıcalıklarıyla Visual Studio 2012 ' i açın.

2. ConfigurationChannelFactory çözümüne (2 proje) sağ tıklayın ve ardından **Özellikler**' i seçin.

3. **Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve ardından **birden fazla başlangıç**projesi ' ne tıklayın.

4. **Hizmet** **projesini listenin** başına **' Başlat ' eylemiyle**taşıyın ve ardından **' Başlat ' eylemine**sahip **Istemci** projesini **, hizmet projesinden** sonra, bu nedenle **istemci** projesi yürütülür.

5. **Tamam**' a tıklayın ve ardından örnek çalıştırmak için F5 tuşuna basın (veya CTRL + F5).

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
