---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel bir WS-Metadata Exchange bağlaması yapılandırma'
title: 'Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: ae9d1932e7539d25c117a98bd130d1def8e691fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743739"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma

Bu makalede, özel bir WS-Metadata Exchange bağlamasının nasıl yapılandırılacağı açıklanmaktadır. Windows Communication Foundation (WCF), sistem tarafından tanımlanan dört meta veri bağlaması içerir, ancak istediğiniz bağlamayı kullanarak meta verileri yayımlayabilirsiniz. Bu makalede, kullanarak meta verilerin nasıl yayımlanacağı gösterilmektedir `wsHttpBinding` . Bu bağlama, meta verileri güvenli bir şekilde gösterme seçeneği sunar. Bu makaledeki kod, [Başlarken](../samples/getting-started-sample.md)' i temel alır.  
  
### <a name="using-a-configuration-file"></a>Yapılandırma dosyası kullanma  
  
1. Hizmetin yapılandırma dosyasında, etiketi içeren bir hizmet davranışı ekleyin `serviceMetadata` :  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. `behaviorConfiguration`Hizmet etiketine bu yeni davranışa başvuran bir öznitelik ekleyin:  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. Adres olarak MEX, `wsHttpBinding` bağlama olarak ve sözleşme olarak belirten bir meta veri uç noktası ekleyin <xref:System.ServiceModel.Description.IMetadataExchange> :  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Meta veri değişimi uç noktasının düzgün çalıştığını doğrulamak için, istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. İstemcinin Main () yönteminde, yeni bir örnek oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient> <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini olarak ayarlayın `true` , çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta veri koleksiyonunu yineleyin:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Kodla yapılandırma  
  
1. <xref:System.ServiceModel.WSHttpBinding>Bağlama örneği oluştur:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Örnek oluşturun <xref:System.ServiceModel.ServiceHost> :  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Hizmet uç noktası ekleyin ve bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek ekleyin:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Daha önce oluşturulmuş bir meta veri değişimi uç noktası ekleyin <xref:System.ServiceModel.WSHttpBinding> :  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Meta veri değişimi uç noktasının düzgün çalıştığını doğrulamak için, istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. İstemcinin Main () yönteminde, yeni bir örnek oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient> <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini olarak ayarlayın `true` , çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta veri koleksiyonu aracılığıyla yineleyin:  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yayımlama Davranışı](../samples/metadata-publishing-behavior.md)
- [Meta Verileri Alma](../samples/retrieve-metadata.md)
- [Meta veri](../feature-details/metadata.md)
- [Meta Verileri Yayımlama](../feature-details/publishing-metadata.md)
- [Meta Veri Uç Noktalarını Yayımlama](../publishing-metadata-endpoints.md)
