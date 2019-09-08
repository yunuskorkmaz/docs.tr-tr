---
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 6cd6e0ce5dc287c826179c152b989b5f7842bb6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795579"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="2b8b8-102">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="2b8b8-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="2b8b8-103">Bu konu, bir MEX uç noktasından bir MEX olmayan bağlama üzerinden meta verilerin nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="2b8b8-104">Bu örnekteki kod, [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="2b8b8-105">Bir MEX olmayan bağlama üzerinden meta verileri almak için</span><span class="sxs-lookup"><span data-stu-id="2b8b8-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="2b8b8-106">MEX uç noktası tarafından kullanılan bağlamayı belirleme.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="2b8b8-107">Windows Communication Foundation (WCF) Hizmetleri için, hizmetin yapılandırma dosyasına erişerek MEX bağlamasını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="2b8b8-108">Bu durumda, MEX bağlaması aşağıdaki hizmet yapılandırmasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2. <span data-ttu-id="2b8b8-109">İstemci yapılandırma dosyasında, aynı özel bağlamayı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="2b8b8-110">Burada istemci Ayrıca, MEX Uç `clientCredentials` noktasından meta veriler istenirken hizmette kimlik doğrulaması yapmak için kullanılacak bir sertifika sağlamak üzere bir davranış tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="2b8b8-111">Özel bir bağlama üzerinden meta veri istemek için Svcutil. exe ' yi kullanırken, MEX uç noktası yapılandırmasını Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasına eklemeniz ve uç nokta yapılandırmasının adı, adresinin URI düzeniyle eşleşmelidir Aşağıdaki kodda gösterildiği gibi, MEX uç noktası.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3. <span data-ttu-id="2b8b8-112">`MetadataExchangeClient` Ve çağrısı`GetMetadata`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="2b8b8-113">Bunu iki şekilde yapabilirsiniz: yapılandırma içinde özel bağlamayı belirtebilir veya aşağıdaki örnekte gösterildiği gibi özel bağlamayı kodda belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="2b8b8-114">Aşağıdaki kodda `WsdlImporter` gösterildiği gibi `ImportAllEndpoints`bir ve çağrısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="2b8b8-115">Bu noktada, hizmet uç noktaları koleksiyonunuz vardır.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="2b8b8-116">Meta verileri içeri aktarma hakkında daha fazla bilgi [için bkz. nasıl yapılır: Meta verileri hizmet uç noktalarına](../feature-details/how-to-import-metadata-into-service-endpoints.md)aktarın.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8b8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b8b8-117">See also</span></span>

- [<span data-ttu-id="2b8b8-118">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="2b8b8-118">Metadata</span></span>](../feature-details/metadata.md)
