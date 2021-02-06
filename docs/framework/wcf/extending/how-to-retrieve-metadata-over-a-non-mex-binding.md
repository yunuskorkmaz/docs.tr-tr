---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: MEX olmayan bağlama üzerinden meta verileri alma'
title: 'Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 521e48d90e9dbed2e0ded61c60af59d063d2b3dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644222"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="4ce62-103">Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="4ce62-103">How to: Retrieve Metadata Over a non-MEX Binding</span></span>

<span data-ttu-id="4ce62-104">Bu konu, bir MEX uç noktasından bir MEX olmayan bağlama üzerinden meta verilerin nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ce62-104">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="4ce62-105">Bu örnekteki kod, [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ce62-105">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="4ce62-106">Bir MEX olmayan bağlama üzerinden meta verileri almak için</span><span class="sxs-lookup"><span data-stu-id="4ce62-106">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="4ce62-107">MEX uç noktası tarafından kullanılan bağlamayı belirleme.</span><span class="sxs-lookup"><span data-stu-id="4ce62-107">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="4ce62-108">Windows Communication Foundation (WCF) Hizmetleri için, hizmetin yapılandırma dosyasına erişerek MEX bağlamasını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce62-108">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="4ce62-109">Bu durumda, MEX bağlaması aşağıdaki hizmet yapılandırmasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ce62-109">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2. <span data-ttu-id="4ce62-110">İstemci yapılandırma dosyasında, aynı özel bağlamayı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4ce62-110">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="4ce62-111">Burada istemci Ayrıca `clientCredentials` , MEX uç noktasından meta veriler istenirken hizmette kimlik doğrulaması yapmak için kullanılacak bir sertifika sağlamak üzere bir davranış tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ce62-111">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="4ce62-112">Özel bir bağlama üzerinden meta veri istemek için Svcutil.exe kullanırken, MEX uç noktası yapılandırmasını Svcutil.exe (Svcutil.exe.config) yapılandırma dosyasına eklemeniz ve uç nokta yapılandırmasının adının, aşağıdaki kodda gösterildiği gibi, MEX uç noktası adresinin URI düzeniyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ce62-112">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3. <span data-ttu-id="4ce62-113">`MetadataExchangeClient`Ve çağrısı oluşturun `GetMetadata` .</span><span class="sxs-lookup"><span data-stu-id="4ce62-113">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="4ce62-114">Bunu iki şekilde yapabilirsiniz: yapılandırma içinde özel bağlamayı belirtebilir veya aşağıdaki örnekte gösterildiği gibi özel bağlamayı kodda belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce62-114">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="4ce62-115">`WsdlImporter` `ImportAllEndpoints` Aşağıdaki kodda gösterildiği gibi bir ve çağrısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ce62-115">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="4ce62-116">Bu noktada, hizmet uç noktaları koleksiyonunuz vardır.</span><span class="sxs-lookup"><span data-stu-id="4ce62-116">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="4ce62-117">Meta verileri içeri aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: meta verileri hizmet uç noktalarına aktarma](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="4ce62-117">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce62-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ce62-118">See also</span></span>

- [<span data-ttu-id="4ce62-119">Meta veri</span><span class="sxs-lookup"><span data-stu-id="4ce62-119">Metadata</span></span>](../feature-details/metadata.md)
