---
title: 'Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851229"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma
Bu konu, özel bir WS-Metadata değişim bağlamasının nasıl yapılandırılacağını açıklar. Windows Communication Foundation (WCF), sistem tarafından tanımlanan dört meta veri bağlaması içerir, ancak istediğiniz bağlamayı kullanarak meta verileri yayımlayabilirsiniz. Bu konu, `wsHttpBinding`kullanarak meta verileri nasıl yayımlayacağınızı gösterir. Bu bağlama, meta verileri güvenli bir şekilde gösterme seçeneği sunar. Bu makaledeki kod, [Başlarken](../samples/getting-started-sample.md)' i temel alır.  
  
### <a name="using-a-configuration-file"></a>Yapılandırma dosyası kullanma  
  
1. Hizmetin yapılandırma dosyasında, `serviceMetadata` etiketi içeren bir hizmet davranışı ekleyin:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Hizmet etiketine `behaviorConfiguration` bu yeni davranışa başvuran bir öznitelik ekleyin:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Adres `wsHttpBinding` olarak MEX, bağlama olarak ve <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme olarak belirten bir meta veri uç noktası ekleyin:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Meta veri değişimi uç noktasının düzgün çalıştığını doğrulamak için istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. İstemcinin Main () yönteminde, <xref:System.ServiceModel.Description.MetadataExchangeClient> yeni bir örnek oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini olarak `true`ayarlayın, çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta veri koleksiyonunu yineleyin:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Kodla yapılandırma  
  
1. <xref:System.ServiceModel.WSHttpBinding> Bağlama örneği oluştur:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <xref:System.ServiceModel.ServiceHost> Örnek oluşturun:  
  
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
  
4. Daha önce <xref:System.ServiceModel.WSHttpBinding> oluşturulmuş bir meta veri değişimi uç noktası ekleyin:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Meta veri değişimi uç noktasının düzgün çalıştığını doğrulamak için, istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. İstemcinin Main () yönteminde, <xref:System.ServiceModel.Description.MetadataExchangeClient> yeni bir örnek oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini olarak `true`ayarlayın, çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta veri koleksiyonu aracılığıyla yineleyin:  
  
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
- [Meta Veriler](../feature-details/metadata.md)
- [Meta Verileri Yayımlama](../feature-details/publishing-metadata.md)
- [Meta Veri Uç Noktalarını Yayımlama](../publishing-metadata-endpoints.md)
