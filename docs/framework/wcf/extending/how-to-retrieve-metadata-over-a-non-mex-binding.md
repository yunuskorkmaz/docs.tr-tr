---
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 4a127e3e2283050018705c85606bd7c03c36de8b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345956"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="d8719-102">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="d8719-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="d8719-103">Bu konu, bir MEX uç noktasından bir MEX olmayan bağlama üzerinden meta verileri alınacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8719-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="d8719-104">Bu örnek kodda dayanır [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d8719-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="d8719-105">Bir MEX olmayan bağlama üzerinden meta verilerini almak için</span><span class="sxs-lookup"><span data-stu-id="d8719-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="d8719-106">MEX uç noktası tarafından kullanılan bağlama belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d8719-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="d8719-107">Windows Communication Foundation (WCF) Hizmetleri, hizmetin yapılandırma dosyası erişerek MEX bağlama belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8719-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="d8719-108">Bu durumda, MEX bağlama aşağıdaki hizmet yapılandırmasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d8719-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2. <span data-ttu-id="d8719-109">İstemci yapılandırma dosyasında aynı özel bağlama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d8719-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="d8719-110">Burada ayrıca istemci tanımlar bir `clientCredentials` MEX uç noktasından metadata isteğinde bulunurken hizmetinde kimlik doğrulaması için kullanılacak bir sertifika sağlamak için davranış.</span><span class="sxs-lookup"><span data-stu-id="d8719-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="d8719-111">Özel bağlama üzerinden meta veri isteği için svcutil.exe kullanma, MEX uç nokta yapılandırması için yapılandırma dosyası için Svcutil.exe (Svcutil.exe.config) eklemelisiniz ve uç nokta yapılandırması adını, adresini URI düzeni eşleşmelidir Aşağıdaki kodda gösterildiği gibi MEX endpoint.</span><span class="sxs-lookup"><span data-stu-id="d8719-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3. <span data-ttu-id="d8719-112">Oluşturma bir `MetadataExchangeClient` ve çağrı `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="d8719-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="d8719-113">Bunu yapmanın iki yolu vardır: özel bağlama yapılandırmasında belirtebilir veya aşağıdaki örnekte gösterildiği gibi kodda özel bağlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8719-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="d8719-114">Oluşturma bir `WsdlImporter` ve çağrı `ImportAllEndpoints`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d8719-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="d8719-115">Bu noktada, hizmet uç noktaları koleksiyonu vardır.</span><span class="sxs-lookup"><span data-stu-id="d8719-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="d8719-116">Meta verileri içeri aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmet uç noktalarına meta verileri alma](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="d8719-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8719-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8719-117">See also</span></span>

- [<span data-ttu-id="d8719-118">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="d8719-118">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
