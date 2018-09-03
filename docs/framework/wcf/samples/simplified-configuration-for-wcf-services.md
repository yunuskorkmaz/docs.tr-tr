---
title: WCF Hizmetleri için Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: ebdf7ab62676bb0c8ac99a5335a3047fcdd5a9b3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482897"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF Hizmetleri için Basitleştirilmiş Yapılandırma
Bu örnek nasıl uygulanacağını ve tipik hizmeti ve Windows Communication Foundation (WCF) kullanarak istemci yapılandırma gösterir. Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.  
  
 Basitleştirilmiş Yapılandırma hizmeti ile iletişim için bir uç noktasını kullanıma sunar, bu hizmeti kullanır [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Öncesinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], aşağıdaki örnek yapılandırma kodda gösterildiği gibi uç noktası genellikle bir yapılandırma dosyasında (Web.config) tanımlanır.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` öğesi, isteğe bağlıdır. Ne zaman bir hizmet tanımlamıyor tüm uç noktalar, her bir temel adres ve uygulanan sözleşme için bir uç nokta eklenir hizmete. Temel adres uç nokta belirlemek için sözleşme adına eklenir ve bağlama adres düzeni tarafından belirlenir. Aşağıdaki kod örneği bir Basitleştirilmiş yapılandırma dosyası gösterir. Adresinden yapılandırıldığı gibi hizmet erişilebilen http://localhost/servicemodelsamples/service.svc aynı bilgisayarda bir istemci tarafından. Hizmete erişmek istemciler için uzak bilgisayarlarda, localhost yerine bir tam etki alanı adı belirtilmelidir. Hizmet meta verileri varsayılan olarak kullanıma sunmuyor. Bu nedenle, hizmet açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aşağıdaki adımları izleyerek örneği çalıştırın:  
  
    1.  Sağ tıklayın **hizmet** seçin ve proje **başlangıç projesi olarak ayarla**, tuşuna **Ctrl + F5**.  
  
    2.  Yedekleme hizmetinin olduğunu onaylamak ve çalışan konsol çıktısı için bekleyin.  
  
    3.  Sağ tıklayın **istemci** seçin ve proje **başlangıç projesi olarak ayarla**, tuşuna **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric Yönetimi örnekleri](https://go.microsoft.com/fwlink/?LinkId=193960)  
 [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
