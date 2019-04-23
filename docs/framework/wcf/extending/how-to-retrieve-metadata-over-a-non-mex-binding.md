---
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 4a127e3e2283050018705c85606bd7c03c36de8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345956"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma
Bu konu, bir MEX uç noktasından bir MEX olmayan bağlama üzerinden meta verileri alınacak açıklar. Bu örnek kodda dayanır [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örnek.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Bir MEX olmayan bağlama üzerinden meta verilerini almak için  
  
1. MEX uç noktası tarafından kullanılan bağlama belirleyin. Windows Communication Foundation (WCF) Hizmetleri, hizmetin yapılandırma dosyası erişerek MEX bağlama belirleyebilirsiniz. Bu durumda, MEX bağlama aşağıdaki hizmet yapılandırmasında tanımlanır.  
  
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
  
2. İstemci yapılandırma dosyasında aynı özel bağlama yapılandırın. Burada ayrıca istemci tanımlar bir `clientCredentials` MEX uç noktasından metadata isteğinde bulunurken hizmetinde kimlik doğrulaması için kullanılacak bir sertifika sağlamak için davranış. Özel bağlama üzerinden meta veri isteği için svcutil.exe kullanma, MEX uç nokta yapılandırması için yapılandırma dosyası için Svcutil.exe (Svcutil.exe.config) eklemelisiniz ve uç nokta yapılandırması adını, adresini URI düzeni eşleşmelidir Aşağıdaki kodda gösterildiği gibi MEX endpoint.  
  
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
  
3. Oluşturma bir `MetadataExchangeClient` ve çağrı `GetMetadata`. Bunu yapmanın iki yolu vardır: özel bağlama yapılandırmasında belirtebilir veya aşağıdaki örnekte gösterildiği gibi kodda özel bağlama belirtebilirsiniz.  
  
    ```  
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
  
4. Oluşturma bir `WsdlImporter` ve çağrı `ImportAllEndpoints`aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. Bu noktada, hizmet uç noktaları koleksiyonu vardır. Meta verileri içeri aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmet uç noktalarına meta verileri alma](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
