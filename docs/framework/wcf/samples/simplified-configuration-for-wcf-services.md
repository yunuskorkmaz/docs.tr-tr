---
title: "WCF Hizmetleri için Basitleştirilmiş Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6f0d73ba01ec51fe2fcd00f33bbd3183e382c74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF Hizmetleri için Basitleştirilmiş Yapılandırma
Bu örnek, uygulama ve tipik hizmeti ve kullanarak istemci yapılandırma gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.  
  
 Basitleştirilmiş yapılandırmada hizmet ile iletişim için bir uç noktasını kullanıma sunar, bu hizmeti kullanan [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Öncesinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], uç nokta yapılandırma dosyasında (Web.config) aşağıdaki örnek yapılandırma kodda gösterildiği gibi tanımlanır.  
  
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
  
 İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` öğesidir isteğe bağlıdır. Ne zaman bir hizmet tanımlamıyor uç nokta, her bir temel adres ve uygulanan sözleşme için bir uç nokta eklenir hizmete. Temel adres uç nokta belirlemek için sözleşme ada eklenir ve bağlama adres düzeni tarafından belirlenir. Aşağıdaki kod örneğinde bir Basitleştirilmiş yapılandırma dosyası gösterir. Yapılandırıldığı şekilde hizmet http://localhost/servicemodelsamples/service.svc aynı bilgisayara bir istemci tarafından erişilebilir. Hizmete erişmek istemciler için uzak bilgisayarlarda, localhost yerine bir tam etki alanı adı belirtilmelidir. Hizmet meta verileri varsayılan olarak kullanıma sunmuyor. Bu nedenle, hizmetin açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı.  
  
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
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Örnek, aşağıdaki adımları izleyerek çalıştırın:  
  
    1.  Sağ tıklayın **hizmet** proje ve seçin **başlangıç projesi olarak ayarla**, tuşuna basarak **Ctrl + F5**.  
  
    2.  Hizmetin çalışır durumda olduğunu onaylamak ve çalışan konsol çıktısı için bekleyin.  
  
    3.  Sağ tıklayın **istemci** proje ve seçin **başlangıç projesi olarak ayarla**, tuşuna basarak **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric Yönetimi örnekleri](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
