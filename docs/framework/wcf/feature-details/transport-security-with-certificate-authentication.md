---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 9ac563ad237749665e9cc53c15aec35f461abfc0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742656"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="d18e0-102">Sertifika Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d18e0-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="d18e0-103">Bu makalede, aktarım güvenliği kullanılırken sunucu ve istemci kimlik doğrulaması için X. 509.440 sertifikalarının kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="d18e0-104">X. 509.440 sertifikaları hakkında daha fazla bilgi için bkz. [x. 509.440 ortak anahtar sertifikaları](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="d18e0-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="d18e0-105">Sertifikalar, genellikle bir üçüncü taraf sertifika veren olan bir sertifika yetkilisi tarafından verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d18e0-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="d18e0-106">Bir Windows Server etki alanında Active Directory Sertifika Hizmetleri, etki alanındaki istemci bilgisayarlara sertifika vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d18e0-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="d18e0-107">Bu senaryoda, hizmet Güvenli Yuva Katmanı (SSL) ile yapılandırılan Internet Information Services (IIS) altında barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="d18e0-108">Hizmet, istemcilerin sunucu kimliğini doğrulamasına izin vermek için bir SSL (X. 509.440) sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="d18e0-109">İstemci Ayrıca hizmetin istemci kimliğini doğrulamasına izin veren bir X. 509.440 sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="d18e0-110">Sunucu sertifikası istemci tarafından güvenilir olmalıdır ve istemcinin sertifikasına sunucu tarafından güvenilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d18e0-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="d18e0-111">Hizmetin ve istemcinin her birinin kimliğini nasıl doğrulayadığına ilişkin gerçek bir mekanizması, bu makalenin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="d18e0-112">Daha fazla bilgi için bkz. Vikipde [dijital imza](https://en.wikipedia.org/wiki/Digital_signature) .</span><span class="sxs-lookup"><span data-stu-id="d18e0-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="d18e0-113">Bu senaryo, aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi deseninin bir listesini uygular.</span><span class="sxs-lookup"><span data-stu-id="d18e0-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="d18e0-114">![Sertifikaları kullanarak güvenli aktarım](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="d18e0-114">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="d18e0-115">Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve bir [SSL sertifikası Ile bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d18e0-115">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="d18e0-116">Aşağıdaki tabloda senaryonun çeşitli özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="d18e0-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="d18e0-117">Characteristic</span></span>|<span data-ttu-id="d18e0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d18e0-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d18e0-119">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="d18e0-119">Security Mode</span></span>|<span data-ttu-id="d18e0-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d18e0-120">Transport</span></span>|  
|<span data-ttu-id="d18e0-121">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d18e0-121">Interoperability</span></span>|<span data-ttu-id="d18e0-122">Mevcut Web hizmeti istemcileri ve hizmetleriyle.</span><span class="sxs-lookup"><span data-stu-id="d18e0-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="d18e0-123">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="d18e0-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="d18e0-124">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="d18e0-124">Authentication (Client)</span></span>|<span data-ttu-id="d18e0-125">Evet (bir SSL sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="d18e0-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="d18e0-126">Evet (bir X. 509.440 sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="d18e0-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="d18e0-127">Veri Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="d18e0-127">Data Integrity</span></span>|<span data-ttu-id="d18e0-128">Evet</span><span class="sxs-lookup"><span data-stu-id="d18e0-128">Yes</span></span>|  
|<span data-ttu-id="d18e0-129">Veri gizliliği</span><span class="sxs-lookup"><span data-stu-id="d18e0-129">Data Confidentiality</span></span>|<span data-ttu-id="d18e0-130">Evet</span><span class="sxs-lookup"><span data-stu-id="d18e0-130">Yes</span></span>|  
|<span data-ttu-id="d18e0-131">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d18e0-131">Transport</span></span>|<span data-ttu-id="d18e0-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="d18e0-132">HTTPS</span></span>|  
|<span data-ttu-id="d18e0-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d18e0-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="d18e0-134">Hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d18e0-134">Configure the Service</span></span>  
 <span data-ttu-id="d18e0-135">Bu senaryodaki hizmet IIS altında barındırıldığından, Web. config dosyası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d18e0-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="d18e0-136">Aşağıdaki Web. config, taşıma güvenliği ve X. 509.440 istemci kimlik bilgilerini kullanmak için <xref:System.ServiceModel.WSHttpBinding> yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d18e0-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>              
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>            
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="d18e0-137">Istemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d18e0-137">Configure the Client</span></span>  
 <span data-ttu-id="d18e0-138">İstemci kodda veya bir App. config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d18e0-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="d18e0-139">Aşağıdaki örnek, kodda istemcisinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d18e0-139">The following example shows how to configure the client in code.</span></span>  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="d18e0-140">Alternatif olarak, aşağıdaki örnekte gösterildiği gibi, istemcisini bir App. config dosyasında yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d18e0-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "   
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d18e0-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d18e0-141">See also</span></span>

- [<span data-ttu-id="d18e0-142">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d18e0-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="d18e0-143">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d18e0-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
