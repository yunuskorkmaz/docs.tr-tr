---
title: "Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4202c0471c681257fa1ab1153d363e59615e10c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma
Bu konuda özel bir WS-Metadata yapılandırmak nasıl anlatılmıştır değişimi bağlaması. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]dört sistem tanımlı meta veri bağlaması içeriyor ancak istediğiniz herhangi bir bağlamayı kullanarak meta verilerini yayımlayabilirsiniz. Bu konuda meta verileri kullanarak yayımlamak nasıl yapacağınızı gösterir `wsHttpBinding`. Bu bağlama meta verileri güvenli bir şekilde gösterme seçeneği sunar. Bu makaledeki kod dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Bir yapılandırma dosyası kullanma  
  
1.  Hizmet yapılandırma dosyasında içeren bir hizmet davranışı eklemek `serviceMetadata` etiketi:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Ekleme bir `behaviorConfiguration` özniteliği bu yeni davranış başvuran hizmet etiketi:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  MEX adresi olarak belirten bir meta veri uç noktası ekleme `wsHttpBinding` bağlama ve <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşme:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  Meta veri exchange uç noktası doğrulamak için çalışma doğru bir uç nokta etiketi ekleyin istemci yapılandırma dosyasında:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  İstemcinin Main() yöntemi yeni bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği, Ayarla kendi <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğine `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve daha sonra döndürülen meta veri toplulukta tekrarlama:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Koduna göre yapılandırma  
  
1.  Oluşturma bir <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> bağlama örneği:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  Oluşturma bir <xref:System.ServiceModel.ServiceHost> örneği:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  Hizmet uç noktası ekleyin ve ekleyin bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  Bir meta veri exchange uç nokta ekleme belirtme <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> daha önce oluşturduğunuz:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  Meta veri exchange uç noktası düzgün çalıştığını doğrulamak için istemci yapılandırma dosyasında bir bitiş etiketi ekleyin:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  İstemcinin Main() yöntemi yeni bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği, Ayarla <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğine `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve daha sonra döndürülen meta veri toplulukta tekrarlama:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri yayımlama davranışı](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [Meta veri alma](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [Meta veriler](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Yayımlama meta veri uç noktaları](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
