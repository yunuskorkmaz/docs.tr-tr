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
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="af654-102">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="af654-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="af654-103">Bu konu, MEX olmayan bir bağlama üzerinden mex bitiş noktasından meta verilerin nasıl alınır açıklar.</span><span class="sxs-lookup"><span data-stu-id="af654-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="af654-104">Bu örnekteki kod, [Özel Güvenli Meta Veri Bitiş Noktası](../samples/custom-secure-metadata-endpoint.md) örneğini temel almıştır.</span><span class="sxs-lookup"><span data-stu-id="af654-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="af654-105">MEX olmayan bir bağlama üzerinden meta veri almak için</span><span class="sxs-lookup"><span data-stu-id="af654-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="af654-106">MEX bitiş noktası tarafından kullanılan bağlamayı belirleyin.</span><span class="sxs-lookup"><span data-stu-id="af654-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="af654-107">Windows Communication Foundation (WCF) hizmetleri için, hizmetin yapılandırma dosyasına erişerek MEX bağlamayı belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af654-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="af654-108">Bu durumda, MEX bağlama aşağıdaki hizmet yapılandırmasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="af654-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2. <span data-ttu-id="af654-109">İstemci yapılandırma dosyasında, aynı özel bağlamayı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="af654-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="af654-110">Burada istemci, MEX `clientCredentials` bitiş noktasından meta veri isteğinde bulunmak üzere hizmete kimlik doğrulaması yapmak için kullanılacak bir sertifika sağlamak için bir davranış da tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af654-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="af654-111">Özel bir bağlama üzerinden meta veri istemek için Svcutil.exe kullanırken, Svcutil.exe (Svcutil.exe.config) için yapılandırma dosyasına MEX uç noktası yapılandırmasını eklemeniz gerekir ve bitiş noktası yapılandırmasının adı adresin URI şemasıyla eşleşmelidir aşağıdaki kodda gösterildiği gibi MEX bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="af654-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3. <span data-ttu-id="af654-112">Bir `MetadataExchangeClient` ve `GetMetadata`çağrı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af654-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="af654-113">Bunu yapmanın iki yolu vardır: yapılandırmada özel bağlamayı belirtebilir veya aşağıdaki örnekte gösterildiği gibi koddaki özel bağlamayı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af654-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="af654-114">Aşağıdaki `WsdlImporter` kodda `ImportAllEndpoints`gösterildiği gibi a ve çağrı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af654-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="af654-115">Bu noktada, hizmet bitiş noktaları koleksiyonuna sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="af654-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="af654-116">Meta veri alma hakkında daha fazla bilgi için [bkz: Meta verileri Hizmet Bitiş Noktalarına Aktarın.](../feature-details/how-to-import-metadata-into-service-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="af654-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af654-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af654-117">See also</span></span>

- [<span data-ttu-id="af654-118">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="af654-118">Metadata</span></span>](../feature-details/metadata.md)
