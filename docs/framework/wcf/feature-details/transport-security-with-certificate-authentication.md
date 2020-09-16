---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
description: Güvenlik aktarım güvenliği kullanılırken, WFC 'nin sunucu ve istemci kimlik doğrulaması için sertifikaları nasıl kullandığı hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 38f7d310be41455dd12460fdfa93d7e624d10c2a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545226"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="c45d6-103">Sertifika Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c45d6-103">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="c45d6-104">Bu makalede, aktarım güvenliği kullanılırken sunucu ve istemci kimlik doğrulaması için X. 509.440 sertifikalarının kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-104">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="c45d6-105">X. 509.440 sertifikaları hakkında daha fazla bilgi için bkz. [x. 509.440 ortak anahtar sertifikaları](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="c45d6-105">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="c45d6-106">Sertifikalar, genellikle bir üçüncü taraf sertifika veren olan bir sertifika yetkilisi tarafından verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c45d6-106">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="c45d6-107">Bir Windows Server etki alanında Active Directory Sertifika Hizmetleri, etki alanındaki istemci bilgisayarlara sertifika vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c45d6-107">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="c45d6-108">Bu senaryoda, hizmet Güvenli Yuva Katmanı (SSL) ile yapılandırılan Internet Information Services (IIS) altında barındırılır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="c45d6-109">Hizmet, istemcilerin sunucu kimliğini doğrulamasına izin vermek için bir SSL (X. 509.440) sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="c45d6-110">İstemci Ayrıca hizmetin istemci kimliğini doğrulamasına izin veren bir X. 509.440 sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="c45d6-111">Sunucu sertifikası istemci tarafından güvenilir olmalıdır ve istemcinin sertifikasına sunucu tarafından güvenilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c45d6-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="c45d6-112">Hizmetin ve istemcinin her birinin kimliğini nasıl doğrulayadığına ilişkin gerçek bir mekanizması, bu makalenin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="c45d6-113">Daha fazla bilgi için bkz. Vikipde [dijital imza](https://en.wikipedia.org/wiki/Digital_signature) .</span><span class="sxs-lookup"><span data-stu-id="c45d6-113">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="c45d6-114">Bu senaryo, aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi deseninin bir listesini uygular.</span><span class="sxs-lookup"><span data-stu-id="c45d6-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="c45d6-115">![Sertifikaları kullanarak güvenli aktarım](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="c45d6-115">![Secure transfer using certificates](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="c45d6-116">Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve bir [SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="c45d6-116">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="c45d6-117">Aşağıdaki tabloda senaryonun çeşitli özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="c45d6-118">Özellik</span><span class="sxs-lookup"><span data-stu-id="c45d6-118">Characteristic</span></span>|<span data-ttu-id="c45d6-119">Description</span><span class="sxs-lookup"><span data-stu-id="c45d6-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c45d6-120">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="c45d6-120">Security Mode</span></span>|<span data-ttu-id="c45d6-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="c45d6-121">Transport</span></span>|  
|<span data-ttu-id="c45d6-122">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="c45d6-122">Interoperability</span></span>|<span data-ttu-id="c45d6-123">Mevcut Web hizmeti istemcileri ve hizmetleriyle.</span><span class="sxs-lookup"><span data-stu-id="c45d6-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="c45d6-124">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="c45d6-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="c45d6-125">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="c45d6-125">Authentication (Client)</span></span>|<span data-ttu-id="c45d6-126">Evet (bir SSL sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="c45d6-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="c45d6-127">Evet (bir X. 509.440 sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="c45d6-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="c45d6-128">Veri bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="c45d6-128">Data Integrity</span></span>|<span data-ttu-id="c45d6-129">Yes</span><span class="sxs-lookup"><span data-stu-id="c45d6-129">Yes</span></span>|  
|<span data-ttu-id="c45d6-130">Veri gizliliği</span><span class="sxs-lookup"><span data-stu-id="c45d6-130">Data Confidentiality</span></span>|<span data-ttu-id="c45d6-131">Yes</span><span class="sxs-lookup"><span data-stu-id="c45d6-131">Yes</span></span>|  
|<span data-ttu-id="c45d6-132">Aktarım</span><span class="sxs-lookup"><span data-stu-id="c45d6-132">Transport</span></span>|<span data-ttu-id="c45d6-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="c45d6-133">HTTPS</span></span>|  
|<span data-ttu-id="c45d6-134">Bağlama</span><span class="sxs-lookup"><span data-stu-id="c45d6-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="c45d6-135">Hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c45d6-135">Configure the Service</span></span>  
 <span data-ttu-id="c45d6-136">Bu senaryodaki hizmet IIS altında barındırıldığından, bir web.config dosyası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c45d6-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="c45d6-137">Aşağıdaki web.config, <xref:System.ServiceModel.WSHttpBinding> ' nin Transport Security ve X. 509.440 istemci kimlik bilgilerini kullanacak şekilde nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c45d6-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="c45d6-138">Istemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c45d6-138">Configure the Client</span></span>  
 <span data-ttu-id="c45d6-139">İstemci kodda veya bir app.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c45d6-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="c45d6-140">Aşağıdaki örnek, kodda istemcisinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c45d6-140">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="c45d6-141">Alternatif olarak, aşağıdaki örnekte gösterildiği gibi bir App.config dosyasında istemcisini yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c45d6-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c45d6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c45d6-142">See also</span></span>

- [<span data-ttu-id="c45d6-143">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="c45d6-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="c45d6-144">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c45d6-144">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
