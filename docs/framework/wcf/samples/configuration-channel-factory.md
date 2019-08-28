---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1b74c15599ebc932a2a0ed46d646b54bec986794
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045652"
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası
Bu örnek, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>kullanımını ele almaktadır. , <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırmasının merkezi yönetimine izin verir. Bu Ayrıca, uygulamanın etki alanı yükleme zamanından sonra yapılandırmanın seçildiği veya değiştiği senaryolarda yararlı olabilir.

## <a name="demonstrates"></a>Gösteriler
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Tartışma
 Bu örnek, varsayılan uygulama yapılandırma <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> dosyasını kullanmak zorunda kalmadan, belirli bir yapılandırma dosyasını istemci uygulamasına eklemek için nasıl kullanılacağını gösterir.

 Örnek iki projeden oluşur. İlk proje, istemcilerden gelen iletileri yanıtlamak için çalışan basit bir hizmettir. İkinci proje, test. config yapılandırma dosyası için bir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> <xref:System.Configuration.ExeConfigurationFileMap> kullanarak iki nesne oluşturan ve hizmeti ile iletişim kurmak için bunları kullanan bir istemci uygulamasıdır. Her iki istemci de test. config dosyasında belirtilen yapılandırmayı kullanarak hizmetle iletişim kurar.

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

4. **Hizmet** projesini listenin başına, **' Başlat ' eylemiyle**taşıyın ve ardından istemci projesi **' Başlat ' eylemiyle**birlikte **hizmet** projesinden sonra , istemci proje yürütülene taşıyın **hizmet** projesinden sonra.

5. **Tamam**' a tıklayın ve ardından örnek çalıştırmak için F5 tuşuna basın (veya CTRL + F5).

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
