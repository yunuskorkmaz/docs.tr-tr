---
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 198c343aa6f25d55e518990dc1dbd2667a8c17ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488094"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma
Bu konuda, bir MEX uç noktasından MEX olmayan bağlama üzerinden meta verilerini almak açıklar. Bu örnek kodda dayanır [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örnek.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>MEX olmayan bağlama üzerinden meta verilerini almak için  
  
1.  MEX bitiş noktası tarafından kullanılan bağlama belirler. Windows Communication Foundation (WCF) hizmetlerini için hizmetin yapılandırma dosyası erişerek MEX bağlama belirleyebilirsiniz. Bu durumda, MEX bağlama aşağıdaki hizmet yapılandırmasında tanımlanır.  
  
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
  
2.  İstemci yapılandırma dosyası, aynı özel bağlama yapılandırın. Burada istemci de tanımlayan bir `clientCredentials` meta verileri MEX uç noktasından isterken hizmete kimlik doğrulaması için kullanılacak bir sertifika sağlamak için davranış. Özel bağlama üzerinden meta veri istemek için svcutil.exe kullanırken Svcutil.exe (Svcutil.exe.config) MEX uç nokta yapılandırması yapılandırma dosyasına eklemelisiniz ve uç nokta yapılandırması adresinin URI şeması adıyla aynı olmalıdır Aşağıdaki kodda gösterildiği gibi MEX endpoint.  
  
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
  
3.  Oluşturma bir `MetadataExchangeClient` ve arama `GetMetadata`. Bunu yapmanın iki yolu vardır: Yapılandırması'nda özel bağlama belirtin veya özel bağlama aşağıdaki örnekte gösterildiği gibi kodda belirtebilirsiniz.  
  
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
  
4.  Oluşturma bir `WsdlImporter` ve arama `ImportAllEndpoints`aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5.  Bu noktada, hizmet uç noktaları koleksiyonu vardır. Meta verileri içe aktarma hakkında daha fazla bilgi için bkz: [nasıl yapılır: hizmet uç noktaları içine meta verileri içeri aktarma](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
