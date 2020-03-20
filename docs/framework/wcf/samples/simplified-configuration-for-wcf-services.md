---
title: WCF Hizmetleri için Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183349"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF Hizmetleri için Basitleştirilmiş Yapılandırma
Bu örnek, Windows Communication Foundation (WCF) kullanarak tipik bir hizmetin ve istemcinin nasıl uygulanacağını ve yapılandırılabildiğini gösterir. Bu örnek, diğer tüm temel teknoloji örneklerinin temelini oluşturur.  
  
 Hizmetle iletişim kurmak için bir bitiş noktası ortaya çıkaran bu hizmet, .NET Framework 4'teki basitleştirilmiş yapılandırmayı kullanır. .NET Framework 4'ten önce, bitiş noktası genellikle aşağıdaki örnek yapılandırma kodunda gösterildiği gibi bir yapılandırma dosyasında (Web.config) tanımlanır.  
  
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
  
 .NET Framework 4'te `<service>` öğe isteğe bağlıdır. Bir hizmet herhangi bir uç nokta tanımlamadığında, uygulanan her temel adres ve sözleşme için bir bitiş noktası hizmete eklenir. Temel adres bitiş noktasını belirlemek için sözleşme adına eklenir ve bağlama adres düzeni tarafından belirlenir. Aşağıdaki kod örneği basitleştirilmiş bir yapılandırma dosyasını gösterir. Yapılandırıldıkça, hizmete aynı bilgisayardaki bir istemci `http://localhost/servicemodelsamples/service.svc` tarafından erişilebilir. Uzak bilgisayarlardaki istemcilerin hizmete erişebilmek için localhost yerine tam nitelikli bir etki alanı adı belirtilmesi gerekir. Hizmet varsayılan olarak meta verileri göstermez. Bu nedenle, hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı açar.  
  
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
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Aşağıdaki adımları izleyerek örneği çalıştırın:  
  
    1. **Hizmet** projesine sağ tıklayın ve **Başlangıç projesi olarak Ayarla'yı**seçin, ardından **Ctrl+F5 tuşuna**basın.  
  
    2. Hizmetin çalışır durumda olduğunu onaylayan konsol çıktısını bekleyin.  
  
    3. **İstemci** projesini sağ tıklatın ve **Başlangıç projesi olarak Ayarla'yı**seçin, ardından **Ctrl+F5 tuşuna**basın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Yönetim Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
