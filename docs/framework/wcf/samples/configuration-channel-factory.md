---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183943"
---
# <a name="configuration-channel-factory"></a>Yapılandırma Kanal Fabrikası
Bu örnek, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.. WCF <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> istemci yapılandırmasının merkezi yönetimine izin verir. Bu, uygulama etki alanı yükleme süresinden sonra yapılandırmanın seçildiği veya değiştirildiği senaryolarda da yararlı olabilir.

## <a name="demonstrates"></a>Gösteriler
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Tartışma
 Bu örnek, varsayılan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> uygulama yapılandırma dosyasını kullanmak zorunda kalmadan, istemci uygulamasına belirli bir yapılandırma dosyası eklemek için nasıl kullanılacağını gösterir.

 Örnek iki projeden oluşur. İlk proje, istemcilerden gelen iletileri yanıtlamak için çalışan basit bir hizmettir. İkinci proje, Test.config yapılandırma <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> dosyası için <xref:System.Configuration.ExeConfigurationFileMap> bir kullanarak iki nesne oluşturan ve bunları hizmetle iletişim kurmak için kullanan bir istemci uygulamasıdır. Her iki istemci de Test.config'de belirtilen yapılandırmayı kullanarak hizmetle iletişim kurar.

 Aşağıdaki kod istemci uygulamasına özel bir yapılandırma dosyası ekler.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Yönetici ayrıcalıkları ile Visual Studio 2012'yi açın.

2. ConfigurationChannelFactory çözümünü (2 proje) sağ tıklatın ve ardından **Özellikler'i**seçin.

3. **Ortak**Özellikler'de, **Başlangıç Projesi'ni**seçin ve ardından **Birden Çok Başlangıç projesi'ni**tıklatın.

4. **Hizmet** projesini, **'Başlat'** eylemiyle listenin başına taşıyın ve Hizmet projesinden sonra Da **bir** de **Eylem 'Başlat'** ile **Istemci** projesini taşıyın, böylece **İstemci** projesi **Hizmet** projesinden sonra yürütülür.

5. **Tamam'ı**tıklatın ve ardından örneği çalıştırmak için F5 (veya CTRL+F5) tuşuna basın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
