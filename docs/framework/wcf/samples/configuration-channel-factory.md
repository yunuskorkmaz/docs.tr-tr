---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: bebdd7e5913fd3bbc1ab88d32e6612b9bc951852
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241154"
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası

Bu örnek, kullanımını ele almaktadır <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> . , <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırmasının merkezi yönetimine izin verir. Bu Ayrıca, uygulamanın etki alanı yükleme zamanından sonra yapılandırmanın seçildiği veya değiştiği senaryolarda yararlı olabilir.

## <a name="demonstrates"></a>Gösteriler

 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Tartışma

 Bu örnek <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> , varsayılan uygulama yapılandırma dosyasını kullanmak zorunda kalmadan, belirli bir yapılandırma dosyasını istemci uygulamasına eklemek için nasıl kullanılacağını gösterir.

 Örnek iki projeden oluşur. İlk proje, istemcilerden gelen iletileri yanıtlamak için çalışan basit bir hizmettir. İkinci proje, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Test.config yapılandırma dosyası için bir kullanarak iki nesne oluşturan <xref:System.Configuration.ExeConfigurationFileMap> ve hizmeti ile iletişim kurmak için bunları kullanan bir istemci uygulamasıdır. Her iki istemci de Test.config belirtilen yapılandırmayı kullanarak hizmetle iletişim kurar.

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

3. **Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve ardından **birden fazla başlangıç** projesi ' ne tıklayın.

4. **Hizmet** **projesini listenin** başına **' Başlat ' eylemiyle** taşıyın ve ardından **' Başlat ' eylemine** sahip **Istemci** projesini **, hizmet projesinden** sonra, bu nedenle **istemci** projesi yürütülür.

5. **Tamam**' a tıklayın ve ardından örnek çalıştırmak için F5 tuşuna basın (veya CTRL + F5).

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
