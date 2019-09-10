---
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 3721657eb72663450261b4bc8627b250b1a4a14e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856038"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma
Bu konu, bir MEX uç noktasından bir MEX olmayan bağlama üzerinden meta verilerin nasıl alınacağını açıklamaktadır. Bu örnekteki kod, [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md) örneğine dayalıdır.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Bir MEX olmayan bağlama üzerinden meta verileri almak için  
  
1. MEX uç noktası tarafından kullanılan bağlamayı belirleme. Windows Communication Foundation (WCF) Hizmetleri için, hizmetin yapılandırma dosyasına erişerek MEX bağlamasını belirleyebilirsiniz. Bu durumda, MEX bağlaması aşağıdaki hizmet yapılandırmasında tanımlanmıştır.  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. İstemci yapılandırma dosyasında, aynı özel bağlamayı yapılandırın. Burada istemci Ayrıca, MEX Uç `clientCredentials` noktasından meta veriler istenirken hizmette kimlik doğrulaması yapmak için kullanılacak bir sertifika sağlamak üzere bir davranış tanımlar. Özel bir bağlama üzerinden meta veri istemek için Svcutil. exe ' yi kullanırken, MEX uç noktası yapılandırmasını Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasına eklemeniz ve uç nokta yapılandırmasının adı, adresinin URI düzeniyle eşleşmelidir Aşağıdaki kodda gösterildiği gibi, MEX uç noktası.  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>    
    </system.serviceModel>  
    ```  
  
3. `MetadataExchangeClient` Ve çağrısı`GetMetadata`oluşturun. Bunu iki şekilde yapabilirsiniz: yapılandırma içinde özel bağlamayı belirtebilir veya aşağıdaki örnekte gösterildiği gibi özel bağlamayı kodda belirtebilirsiniz.  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. Aşağıdaki kodda `WsdlImporter` gösterildiği gibi `ImportAllEndpoints`bir ve çağrısı oluşturun.  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. Bu noktada, hizmet uç noktaları koleksiyonunuz vardır. Meta verileri içeri aktarma hakkında daha fazla bilgi [için bkz. nasıl yapılır: Meta verileri hizmet uç noktalarına](../feature-details/how-to-import-metadata-into-service-endpoints.md)aktarın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../feature-details/metadata.md)
