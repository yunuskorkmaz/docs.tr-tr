---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 65d076a9fef716fca4fe87df6bc5c7773e2dda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499121"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="111c8-102">Temel Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="111c8-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="111c8-103">Aşağıdaki çizimde, bir Windows Communication Foundation (WCF) hizmetini ve istemci gösterir.</span><span class="sxs-lookup"><span data-stu-id="111c8-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="111c8-104">Güvenli Yuva Katmanı (SSL) için kullanılan geçerli bir X.509 sertifikası sunucu gerekir ve istemcilerin sunucu sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="111c8-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="111c8-105">Ayrıca, Web hizmeti, kullanılabilir bir SSL uygulaması zaten içeriyor.</span><span class="sxs-lookup"><span data-stu-id="111c8-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="111c8-106">Daha fazla bilgi için etkinleştirme temel kimlik doğrulaması hakkında Internet Information Services (IIS) üzerinde [ http://go.microsoft.com/fwlink/?LinkId=83822 ](http://go.microsoft.com/fwlink/?LinkId=83822).</span><span class="sxs-lookup"><span data-stu-id="111c8-106">For more information about enabling basic authentication on Internet Information Services (IIS), see [http://go.microsoft.com/fwlink/?LinkId=83822](http://go.microsoft.com/fwlink/?LinkId=83822).</span></span>  
  
 <span data-ttu-id="111c8-107">![Taşıma güvenliği temel kimlik doğrulaması ile](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span><span class="sxs-lookup"><span data-stu-id="111c8-107">![Transport security with basic authentication](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span></span>  
  
|<span data-ttu-id="111c8-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="111c8-108">Characteristic</span></span>|<span data-ttu-id="111c8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="111c8-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="111c8-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="111c8-110">Security Mode</span></span>|<span data-ttu-id="111c8-111">Taşıma</span><span class="sxs-lookup"><span data-stu-id="111c8-111">Transport</span></span>|  
|<span data-ttu-id="111c8-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="111c8-112">Interoperability</span></span>|<span data-ttu-id="111c8-113">Mevcut Web hizmeti istemcileri ve Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="111c8-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="111c8-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="111c8-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="111c8-115">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="111c8-115">Authentication (Client)</span></span>|<span data-ttu-id="111c8-116">Evet (HTTPS kullanarak)</span><span class="sxs-lookup"><span data-stu-id="111c8-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="111c8-117">Evet (kullanıcı adı/parola)</span><span class="sxs-lookup"><span data-stu-id="111c8-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="111c8-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="111c8-118">Integrity</span></span>|<span data-ttu-id="111c8-119">Evet</span><span class="sxs-lookup"><span data-stu-id="111c8-119">Yes</span></span>|  
|<span data-ttu-id="111c8-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="111c8-120">Confidentiality</span></span>|<span data-ttu-id="111c8-121">Evet</span><span class="sxs-lookup"><span data-stu-id="111c8-121">Yes</span></span>|  
|<span data-ttu-id="111c8-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="111c8-122">Transport</span></span>|<span data-ttu-id="111c8-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="111c8-123">HTTPS</span></span>|  
|<span data-ttu-id="111c8-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="111c8-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="111c8-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="111c8-125">Service</span></span>  
 <span data-ttu-id="111c8-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="111c8-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="111c8-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="111c8-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="111c8-128">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="111c8-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="111c8-129">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="111c8-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="111c8-130">Kod</span><span class="sxs-lookup"><span data-stu-id="111c8-130">Code</span></span>  
 <span data-ttu-id="111c8-131">Aşağıdaki kod, bir Windows etki alanı kullanıcı adı ve parola aktarımı güvenlik için kullandığı bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="111c8-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="111c8-132">Hizmeti için istemci kimlik doğrulaması için bir X.509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="111c8-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="111c8-133">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="111c8-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="111c8-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="111c8-134">Configuration</span></span>  
 <span data-ttu-id="111c8-135">Bir hizmet ile aktarım düzeyinde güvenlik temel kimlik doğrulaması kullanacak şekilde yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="111c8-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="111c8-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="111c8-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="111c8-137">Kod</span><span class="sxs-lookup"><span data-stu-id="111c8-137">Code</span></span>  
 <span data-ttu-id="111c8-138">Aşağıdaki kod kullanıcı adını ve parolayı içeren istemci kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="111c8-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="111c8-139">Kullanıcının geçerli bir Windows kullanıcı adı ve parola sağlamalısınız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="111c8-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="111c8-140">Kullanıcı adı ve parola döndürecek olan kodu burada gösterilmiyor.</span><span class="sxs-lookup"><span data-stu-id="111c8-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="111c8-141">Bir iletişim kutusu veya diğer arabirimi kullanıcıdan bilgi sorgulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="111c8-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="111c8-142">Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="111c8-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="111c8-143">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="111c8-143">Configuration</span></span>  
 <span data-ttu-id="111c8-144">Aşağıdaki kod istemci yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="111c8-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="111c8-145">Kullanıcı adını ve parolasını ayarlamak için yapılandırma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="111c8-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="111c8-146">Burada gösterilen yapılandırması, kullanıcı adını ve parolasını ayarlamak için kod kullanarak yükseltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="111c8-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="111c8-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="111c8-147">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [<span data-ttu-id="111c8-148">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="111c8-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="111c8-149">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="111c8-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="111c8-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="111c8-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="111c8-151">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="111c8-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [<span data-ttu-id="111c8-152">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="111c8-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
