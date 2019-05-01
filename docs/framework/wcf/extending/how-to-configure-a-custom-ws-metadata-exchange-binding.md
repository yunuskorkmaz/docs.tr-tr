---
title: 'Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 51681e258e6a21b3a7ae604d1c0ef65d320bfb4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991230"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma
Bu konu, özel bir WS-Metadata yapılandırma açıklayacak değişimi bağlaması. Windows Communication Foundation (WCF) dört sistem tarafından tanımlanan meta veri bağlamaları içerir, ancak meta veriler, istediğiniz herhangi bir bağlamayı kullanarak yayımlayabilirsiniz. Bu konuda, meta verileri kullanarak yayımlamak nasıl gösterilecektir `wsHttpBinding`. Bu bağlama, güvenli bir şekilde meta verileri kullanıma sunduğundan seçeneği sunar. Bu makalede kod dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Yapılandırma dosyası kullanma  
  
1. Hizmet yapılandırma dosyasında içeren bir hizmet davranışını ekleyin `serviceMetadata` etiketi:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Ekleme bir `behaviorConfiguration` özniteliği bu yeni davranış başvuran hizmet etiketi:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. MEX adres olarak belirten bir meta veri uç noktası ekleme `wsHttpBinding` bağlama olarak ve <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşme:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Meta veri değişimi uç noktası olduğunu doğrulamak için çalışma doğru bir uç nokta etiket eklemede istemci yapılandırma dosyasında:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. Yeni bir istemcinin Main() yöntemi oluşturma <xref:System.ServiceModel.Description.MetadataExchangeClient> örnek olarak ayarlayın, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta verileri koleksiyonu yineleme:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Kod ile yapılandırma  
  
1. Oluşturma bir <xref:System.ServiceModel.WSHttpBinding> bağlama örneği:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Oluşturma bir <xref:System.ServiceModel.ServiceHost> örneği:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Hizmet uç noktası ekleme ve ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Meta veri değişimi uç noktası ekleme belirtme <xref:System.ServiceModel.WSHttpBinding> daha önce oluşturulan:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Meta veri değişimi uç noktası düzgün çalıştığını doğrulamak için istemci yapılandırma dosyasında bir bitiş etiketi ekleyin:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. Yeni bir istemcinin Main() yöntemi oluşturma <xref:System.ServiceModel.Description.MetadataExchangeClient> örnek olarak ayarlayın <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta verileri koleksiyonu yineleme:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yayımlama Davranışı](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
- [Meta Verileri Alma](../../../../docs/framework/wcf/samples/retrieve-metadata.md)
- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [Meta Veri Uç Noktalarını Yayımlama](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
