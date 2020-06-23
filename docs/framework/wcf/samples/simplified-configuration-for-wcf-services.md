---
title: WCF Hizmetleri için Basitleştirilmiş Yapılandırma
description: WCF kullanarak tipik bir hizmeti ve istemciyi uygulamayı ve yapılandırmayı öğrenin. Hizmet, bir yapılandırma dosyasında belirtilen bir uç nokta kullanarak iletişim kurar.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246226"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF Hizmetleri için Basitleştirilmiş Yapılandırma
Bu örnek, Windows Communication Foundation (WCF) kullanarak tipik bir hizmetin ve istemcinin nasıl uygulanacağını ve yapılandırılacağını gösterir. Bu örnek, diğer tüm temel teknoloji örnekleri için temeldir.  
  
 Hizmetle iletişim kurmak için bir uç nokta sunan bu hizmet, .NET Framework 4 ' te Basitleştirilmiş yapılandırmayı kullanır. .NET Framework 4 ' ten önce, uç nokta genellikle aşağıdaki örnek yapılandırma kodunda gösterildiği gibi bir yapılandırma dosyasında (Web.config) tanımlanmıştır.  
  
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
  
 .NET Framework 4 ' te, `<service>` öğesi isteğe bağlıdır. Bir hizmet herhangi bir uç nokta tanımlamıyorsa, uygulanan her temel adres ve sözleşme için bir uç nokta hizmete eklenir. Bitiş noktasını ve bağlamanın adres düzeni tarafından belirlendiği temel adres, sözleşmenin adına eklenir. Aşağıdaki kod örneği, Basitleştirilmiş bir yapılandırma dosyasını göstermektedir. Yapılandırıldığı gibi, hizmete `http://localhost/servicemodelsamples/service.svc` aynı bilgisayardaki bir istemci tarafından erişilebilir. Uzak bilgisayarlardaki istemcilerin hizmete erişmesi için localhost yerine tam etki alanı adı belirtilmelidir. Hizmet varsayılan olarak meta verileri kullanıma sunmaz. Bu nedenle hizmet, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı etkinleştirir.  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Aşağıdaki adımları izleyerek örneği çalıştırın:  
  
    1. **Hizmet** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin ve ardından **CTRL + F5**tuşlarına basın.  
  
    2. Hizmetin çalışır olduğunu onaylayan konsol çıkışının tamamlanmasını bekleyin.  
  
    3. **İstemci** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin ve ardından **CTRL + F5**tuşlarına basın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric yönetim örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Basitleştirilmiş Yapılandırma](../simplified-configuration.md)
