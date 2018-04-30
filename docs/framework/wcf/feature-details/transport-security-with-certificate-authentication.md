---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
caps.latest.revision: 20
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 19b54739d82fe7363319211d3f753416e0966aed
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="cf004-102">Sertifika Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cf004-102">Transport Security with Certificate Authentication</span></span>
<span data-ttu-id="cf004-103">Bu konu, taşıma güvenliği kullanırken X.509 sertifikalarını server ve istemci kimlik doğrulaması kullanarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf004-103">This topic discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="cf004-104">X.509 hakkında daha fazla bilgi için bkz: sertifikalar [X.509 ortak anahtar sertifikaları](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="cf004-104">For more information about X.509 certificates see [X.509 Public Key Certificates](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx).</span></span> <span data-ttu-id="cf004-105">Sertifika bir üçüncü taraf veren sertifikalarının görülür bir sertifika yetkilisi tarafından verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf004-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="cf004-106">Bir Windows Server etki alanı Active Directory Sertifika Hizmetleri, istemci bilgisayarlar etki alanı için sertifikalar vermek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf004-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="cf004-107">Daha fazla bilgi için bkz: [Windows 2008 R2 Sertifika Hizmetleri](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="cf004-107">For more information see [Windows 2008 R2 Certificate Services](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span></span> <span data-ttu-id="cf004-108">Bu senaryoda, hizmetin altında Internet Information Services (Güvenli Yuva Katmanı (SSL) ile yapılandırılmış olan IIS) barındırılıyor.</span><span class="sxs-lookup"><span data-stu-id="cf004-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="cf004-109">Hizmet, istemcilerin sunucunun kimliğini doğrulamak bir SSL (X.509) sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="cf004-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="cf004-110">İstemci aynı zamanda istemci kimliğini doğrulamak hizmet veren bir X.509 sertifikası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="cf004-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="cf004-111">İstemci tarafından sunucunun sertifikası güvenilir olması gerekir ve istemcinin sertifika sunucusu tarafından güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf004-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="cf004-112">Gerçek mekanizması nasıl hizmeti istemci doğrular ve birbirlerinin kimliğini, bu konu kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="cf004-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this topic.</span></span> <span data-ttu-id="cf004-113">Daha fazla bilgi için bkz: [wikipedia'da dijital imza](http://go.microsoft.com/fwlink/?LinkId=253157).</span><span class="sxs-lookup"><span data-stu-id="cf004-113">For more information see [Digital Signature on Wikipedia](http://go.microsoft.com/fwlink/?LinkId=253157).</span></span>  
  
 <span data-ttu-id="cf004-114">Bu senaryo tarafından Aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt ileti deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="cf004-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="cf004-115">![Güvenli aktarım sertifikaları kullanarak](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="cf004-115">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="cf004-116">Bir sertifika bir hizmetle kullanma hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="cf004-116">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="cf004-117">Aşağıdaki tabloda senaryosu çeşitli özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf004-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="cf004-118">Özelliği</span><span class="sxs-lookup"><span data-stu-id="cf004-118">Characteristic</span></span>|<span data-ttu-id="cf004-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf004-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cf004-120">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="cf004-120">Security Mode</span></span>|<span data-ttu-id="cf004-121">Taşıma</span><span class="sxs-lookup"><span data-stu-id="cf004-121">Transport</span></span>|  
|<span data-ttu-id="cf004-122">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="cf004-122">Interoperability</span></span>|<span data-ttu-id="cf004-123">Mevcut Web hizmeti istemcileri ve Hizmetleri ile.</span><span class="sxs-lookup"><span data-stu-id="cf004-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="cf004-124">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="cf004-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="cf004-125">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="cf004-125">Authentication (Client)</span></span>|<span data-ttu-id="cf004-126">Evet (bir SSL sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="cf004-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="cf004-127">Evet (bir X.509 sertifikası kullanarak)</span><span class="sxs-lookup"><span data-stu-id="cf004-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="cf004-128">Veri bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="cf004-128">Data Integrity</span></span>|<span data-ttu-id="cf004-129">Evet</span><span class="sxs-lookup"><span data-stu-id="cf004-129">Yes</span></span>|  
|<span data-ttu-id="cf004-130">Veri gizliliği</span><span class="sxs-lookup"><span data-stu-id="cf004-130">Data Confidentiality</span></span>|<span data-ttu-id="cf004-131">Evet</span><span class="sxs-lookup"><span data-stu-id="cf004-131">Yes</span></span>|  
|<span data-ttu-id="cf004-132">Taşıma</span><span class="sxs-lookup"><span data-stu-id="cf004-132">Transport</span></span>|<span data-ttu-id="cf004-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="cf004-133">HTTPS</span></span>|  
|<span data-ttu-id="cf004-134">Bağlama</span><span class="sxs-lookup"><span data-stu-id="cf004-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="cf004-135">Hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cf004-135">Configure the Service</span></span>  
 <span data-ttu-id="cf004-136">Bu senaryoda hizmeti IIS altında barındırılan olduğundan, bir web.config dosyası ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="cf004-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="cf004-137">Aşağıdaki web.config nasıl yapılandırılacağını göstermektedir <xref:System.ServiceModel.WSHttpBinding> taşıma güvenliği ve X.509 istemci kimlik bilgilerini kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="cf004-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="cf004-138">İstemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cf004-138">Configure the Client</span></span>  
 <span data-ttu-id="cf004-139">İstemci kodu veya bir app.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf004-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="cf004-140">Aşağıdaki örnek kodda istemciyi Yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cf004-140">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="cf004-141">Alternatif olarak aşağıdaki örnekte gösterildiği gibi bir App.config dosyasında istemci yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cf004-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf004-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf004-142">See Also</span></span>  
 [<span data-ttu-id="cf004-143">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cf004-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="cf004-144">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="cf004-144">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
