---
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: a006795c87a2ae845d03db90dce296692c4339fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186440"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma
Bu konu, MEX olmayan bir bağlama üzerinden mex bitiş noktasından meta verilerin nasıl alınır açıklar. Bu örnekteki kod, [Özel Güvenli Meta Veri Bitiş Noktası](../samples/custom-secure-metadata-endpoint.md) örneğini temel almıştır.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>MEX olmayan bir bağlama üzerinden meta veri almak için  
  
1. MEX bitiş noktası tarafından kullanılan bağlamayı belirleyin. Windows Communication Foundation (WCF) hizmetleri için, hizmetin yapılandırma dosyasına erişerek MEX bağlamayı belirleyebilirsiniz. Bu durumda, MEX bağlama aşağıdaki hizmet yapılandırmasında tanımlanır.  
  
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
  
2. İstemci yapılandırma dosyasında, aynı özel bağlamayı yapılandırın. Burada istemci, MEX `clientCredentials` bitiş noktasından meta veri isteğinde bulunmak üzere hizmete kimlik doğrulaması yapmak için kullanılacak bir sertifika sağlamak için bir davranış da tanımlar. Özel bir bağlama üzerinden meta veri istemek için Svcutil.exe kullanırken, Svcutil.exe (Svcutil.exe.config) için yapılandırma dosyasına MEX uç noktası yapılandırmasını eklemeniz gerekir ve bitiş noktası yapılandırmasının adı adresin URI şemasıyla eşleşmelidir aşağıdaki kodda gösterildiği gibi MEX bitiş noktası.  
  
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
  
3. Bir `MetadataExchangeClient` ve `GetMetadata`çağrı oluşturun. Bunu yapmanın iki yolu vardır: yapılandırmada özel bağlamayı belirtebilir veya aşağıdaki örnekte gösterildiği gibi koddaki özel bağlamayı belirtebilirsiniz.  
  
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
  
4. Aşağıdaki `WsdlImporter` kodda `ImportAllEndpoints`gösterildiği gibi a ve çağrı oluşturun.  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. Bu noktada, hizmet bitiş noktaları koleksiyonuna sahipsiniz. Meta veri alma hakkında daha fazla bilgi için [bkz: Meta verileri Hizmet Bitiş Noktalarına Aktarın.](../feature-details/how-to-import-metadata-into-service-endpoints.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta veriler](../feature-details/metadata.md)
