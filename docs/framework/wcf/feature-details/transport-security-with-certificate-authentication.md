---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184324"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="46b02-102">Sertifika Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="46b02-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="46b02-103">Bu makalede, aktarım güvenliği kullanırken sunucu ve istemci kimlik doğrulaması için X.509 sertifikaları nın kullanılması anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46b02-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="46b02-104">X.509 sertifikaları hakkında daha fazla bilgi için [Bkz. X.509 Ortak Anahtar Sertifikaları.](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates)</span><span class="sxs-lookup"><span data-stu-id="46b02-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="46b02-105">Sertifikalar, genellikle sertifikaların üçüncü taraf vereni olan bir sertifika yetkilisi tarafından verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="46b02-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="46b02-106">Bir Windows Server etki alanında, Etkin Dizin Sertifika Hizmetleri etki alanında istemci bilgisayarlara sertifika vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46b02-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="46b02-107">Bu senaryoda, hizmet Güvenli Soketkatmanı (SSL) ile yapılandırılan Internet Information Services (IIS) altında barındırılır.</span><span class="sxs-lookup"><span data-stu-id="46b02-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="46b02-108">Hizmet, istemcilerin sunucunun kimliğini doğrulamasına olanak sağlamak için bir SSL (X.509) sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="46b02-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="46b02-109">İstemci ayrıca, hizmetin istemcinin kimliğini doğrulamasına olanak tanıyan bir X.509 sertifikasıyla da yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="46b02-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="46b02-110">Sunucunun sertifikası istemci tarafından güvenilmeli ve istemcinin sertifikası sunucu tarafından güvenilmelidir.</span><span class="sxs-lookup"><span data-stu-id="46b02-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="46b02-111">Hizmetin ve istemcinin birbirlerinin kimliğini doğrulama sının gerçek mekaniği bu makalenin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="46b02-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="46b02-112">Daha fazla bilgi için Wikipedia'da [Dijital İmza'ya](https://en.wikipedia.org/wiki/Digital_signature) bakın.</span><span class="sxs-lookup"><span data-stu-id="46b02-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="46b02-113">Bu senaryo, aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="46b02-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="46b02-114">![Sertifikaları kullanarak güvenli aktarım](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="46b02-114">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="46b02-115">Hizmetli bir sertifika kullanma hakkında daha fazla bilgi için bkz: [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [Nasıl Yapılandırılabilen: SSL Sertifikası olan bir Bağlantı Noktasını Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)</span><span class="sxs-lookup"><span data-stu-id="46b02-115">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="46b02-116">Aşağıdaki tabloda senaryonun çeşitli özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46b02-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="46b02-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="46b02-117">Characteristic</span></span>|<span data-ttu-id="46b02-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46b02-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="46b02-119">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="46b02-119">Security Mode</span></span>|<span data-ttu-id="46b02-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="46b02-120">Transport</span></span>|  
|<span data-ttu-id="46b02-121">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="46b02-121">Interoperability</span></span>|<span data-ttu-id="46b02-122">Mevcut Web hizmeti istemcileri ve hizmetleri ile.</span><span class="sxs-lookup"><span data-stu-id="46b02-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="46b02-123">Kimlik Doğrulama (Sunucu)</span><span class="sxs-lookup"><span data-stu-id="46b02-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="46b02-124">Kimlik Doğrulama (İstemci)</span><span class="sxs-lookup"><span data-stu-id="46b02-124">Authentication (Client)</span></span>|<span data-ttu-id="46b02-125">Evet (SSL sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="46b02-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="46b02-126">Evet (X.509 sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="46b02-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="46b02-127">Veri Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="46b02-127">Data Integrity</span></span>|<span data-ttu-id="46b02-128">Evet</span><span class="sxs-lookup"><span data-stu-id="46b02-128">Yes</span></span>|  
|<span data-ttu-id="46b02-129">Veri Gizliliği</span><span class="sxs-lookup"><span data-stu-id="46b02-129">Data Confidentiality</span></span>|<span data-ttu-id="46b02-130">Evet</span><span class="sxs-lookup"><span data-stu-id="46b02-130">Yes</span></span>|  
|<span data-ttu-id="46b02-131">Aktarım</span><span class="sxs-lookup"><span data-stu-id="46b02-131">Transport</span></span>|<span data-ttu-id="46b02-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="46b02-132">HTTPS</span></span>|  
|<span data-ttu-id="46b02-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="46b02-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="46b02-134">Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46b02-134">Configure the Service</span></span>  
 <span data-ttu-id="46b02-135">Bu senaryodaki hizmet IIS altında barındırıldığından, bir web.config dosyasıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="46b02-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="46b02-136">Aşağıdaki web.config taşıma güvenliği ve <xref:System.ServiceModel.WSHttpBinding> X.509 istemci kimlik bilgilerini kullanmak için nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46b02-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="46b02-137">İstemciyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46b02-137">Configure the Client</span></span>  
 <span data-ttu-id="46b02-138">İstemci kod veya app.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="46b02-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="46b02-139">Aşağıdaki örnekte, istemcinin kod da nasıl yapılandırılabildiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46b02-139">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="46b02-140">Alternatif olarak, istemciyi aşağıdaki örnekte gösterildiği gibi bir App.config dosyasında yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="46b02-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46b02-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46b02-141">See also</span></span>

- [<span data-ttu-id="46b02-142">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="46b02-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="46b02-143">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="46b02-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
