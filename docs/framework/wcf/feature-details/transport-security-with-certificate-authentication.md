---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2da7a304af613920449e925e3bb43b350f556e6a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786511"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="956f4-102">Sertifika Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="956f4-102">Transport Security with Certificate Authentication</span></span>
<span data-ttu-id="956f4-103">Bu konuda, X.509 sertifikaları aktarım güvenliği kullanarak sunucu ve istemci kimlik doğrulaması kullanılarak anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="956f4-103">This topic discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="956f4-104">X.509 hakkında daha fazla bilgi için bkz: sertifikaları [X.509 ortak anahtar sertifikaları](https://msdn.microsoft.com/library/bb540819\(VS.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="956f4-104">For more information about X.509 certificates see [X.509 Public Key Certificates](https://msdn.microsoft.com/library/bb540819\(VS.85\).aspx).</span></span> <span data-ttu-id="956f4-105">Sertifikaları çoğunlukla sertifika bir üçüncü taraf veren olduğu bir sertifika yetkilisi tarafından verilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="956f4-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="956f4-106">Bir Windows Server etki alanı Active Directory Sertifika Hizmetleri, etki alanındaki istemci bilgisayarlar için sertifikaları vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="956f4-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="956f4-107">Daha fazla bilgi için [Windows 2008 R2 Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="956f4-107">For more information see [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span></span> <span data-ttu-id="956f4-108">Bu senaryoda, hizmetin altında Internet Information Services (Güvenli Yuva Katmanı (SSL) ile yapılandırılmış olan IIS) barındırılır.</span><span class="sxs-lookup"><span data-stu-id="956f4-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="956f4-109">Hizmet, istemcilerin kimliğini doğrulamak bir SSL (X.509) sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="956f4-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="956f4-110">İstemci, istemcinin kimliğini doğrulamak hizmet veren bir X.509 sertifikası ile de yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="956f4-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="956f4-111">Sunucu sertifikasının istemci tarafından güvenilir olması gerekir ve istemcinin sertifika sunucusu tarafından güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="956f4-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="956f4-112">Gerçek mekanizması nasıl hizmet ve istemci doğrular birbirlerinin kimliğini, bu konunun kapsamı dışındadır ' dir.</span><span class="sxs-lookup"><span data-stu-id="956f4-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this topic.</span></span> <span data-ttu-id="956f4-113">Daha fazla bilgi için [wikipedia dijital imza](https://go.microsoft.com/fwlink/?LinkId=253157).</span><span class="sxs-lookup"><span data-stu-id="956f4-113">For more information see [Digital Signature on Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).</span></span>  
  
 <span data-ttu-id="956f4-114">Bu senaryo tarafından Aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi desenini uygular.</span><span class="sxs-lookup"><span data-stu-id="956f4-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="956f4-115">![Güvenli aktarım sertifikaları kullanarak](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="956f4-115">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="956f4-116">Bir sertifika bir hizmetle kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="956f4-116">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="956f4-117">Aşağıdaki tabloda çeşitli senaryo özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="956f4-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="956f4-118">Özelliği</span><span class="sxs-lookup"><span data-stu-id="956f4-118">Characteristic</span></span>|<span data-ttu-id="956f4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="956f4-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="956f4-120">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="956f4-120">Security Mode</span></span>|<span data-ttu-id="956f4-121">Taşıma</span><span class="sxs-lookup"><span data-stu-id="956f4-121">Transport</span></span>|  
|<span data-ttu-id="956f4-122">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="956f4-122">Interoperability</span></span>|<span data-ttu-id="956f4-123">Mevcut Web hizmeti istemcileri ve Hizmetleri ile.</span><span class="sxs-lookup"><span data-stu-id="956f4-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="956f4-124">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="956f4-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="956f4-125">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="956f4-125">Authentication (Client)</span></span>|<span data-ttu-id="956f4-126">Evet (bir SSL sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="956f4-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="956f4-127">Evet (bir X.509 sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="956f4-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="956f4-128">Veri bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="956f4-128">Data Integrity</span></span>|<span data-ttu-id="956f4-129">Evet</span><span class="sxs-lookup"><span data-stu-id="956f4-129">Yes</span></span>|  
|<span data-ttu-id="956f4-130">Veri gizliliği</span><span class="sxs-lookup"><span data-stu-id="956f4-130">Data Confidentiality</span></span>|<span data-ttu-id="956f4-131">Evet</span><span class="sxs-lookup"><span data-stu-id="956f4-131">Yes</span></span>|  
|<span data-ttu-id="956f4-132">Taşıma</span><span class="sxs-lookup"><span data-stu-id="956f4-132">Transport</span></span>|<span data-ttu-id="956f4-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="956f4-133">HTTPS</span></span>|  
|<span data-ttu-id="956f4-134">Bağlama</span><span class="sxs-lookup"><span data-stu-id="956f4-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="956f4-135">Hizmet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="956f4-135">Configure the Service</span></span>  
 <span data-ttu-id="956f4-136">Bu senaryoda hizmeti IIS altında barındırıldığından, web.config dosyasına yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="956f4-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="956f4-137">Aşağıdaki web.config nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.WSHttpBinding> aktarım güvenliği ve X.509 istemci kimlik bilgileri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="956f4-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="956f4-138">İstemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="956f4-138">Configure the Client</span></span>  
 <span data-ttu-id="956f4-139">İstemci kodu veya bir app.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="956f4-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="956f4-140">Aşağıdaki örnek kodda istemciyi Yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="956f4-140">The following example shows how to configure the client in code.</span></span>  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
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
  
 <span data-ttu-id="956f4-141">Alternatif olarak aşağıdaki örnekte gösterildiği gibi bir App.config dosyasında istemci yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="956f4-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="956f4-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="956f4-142">See Also</span></span>  
 [<span data-ttu-id="956f4-143">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="956f4-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="956f4-144">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="956f4-144">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
