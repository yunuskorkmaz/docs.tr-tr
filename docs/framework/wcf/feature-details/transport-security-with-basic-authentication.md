---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
description: Bir WCF hizmeti ve istemcisi için temel kimlik doğrulaması gösteren bu WCF senaryosunu inceleyin. Hizmetin, istemcinin güvendiği geçerli bir sertifikası olması gerekir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 2add8c21ca8ade4b530e0e6b1b3c5bba66e100ab
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556791"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="adae0-104">Temel Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="adae0-104">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="adae0-105">Aşağıdaki çizimde bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="adae0-105">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="adae0-106">Sunucu, Güvenli Yuva Katmanı (SSL) için kullanılabilecek geçerli bir X. 509.440 sertifikasına ihtiyaç duyuyor ve istemcilerin sunucunun sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="adae0-106">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="adae0-107">Ayrıca, Web hizmeti zaten kullanılabilecek bir SSL uygulamasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="adae0-107">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="adae0-108">Internet Information Services (IIS) üzerinde temel kimlik doğrulamasını etkinleştirme hakkında daha fazla bilgi için bkz <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> ..</span><span class="sxs-lookup"><span data-stu-id="adae0-108">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Temel kimlik doğrulaması ile taşıma güvenliğini gösteren ekran görüntüsü.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="adae0-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="adae0-110">Characteristic</span></span>|<span data-ttu-id="adae0-111">Description</span><span class="sxs-lookup"><span data-stu-id="adae0-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="adae0-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="adae0-112">Security Mode</span></span>|<span data-ttu-id="adae0-113">Aktarım</span><span class="sxs-lookup"><span data-stu-id="adae0-113">Transport</span></span>|  
|<span data-ttu-id="adae0-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="adae0-114">Interoperability</span></span>|<span data-ttu-id="adae0-115">Mevcut Web hizmeti istemcileri ve hizmetleriyle</span><span class="sxs-lookup"><span data-stu-id="adae0-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="adae0-116">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="adae0-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="adae0-117">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="adae0-117">Authentication (Client)</span></span>|<span data-ttu-id="adae0-118">Evet (HTTPS kullanarak)</span><span class="sxs-lookup"><span data-stu-id="adae0-118">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="adae0-119">Evet (Kullanıcı adı/parola aracılığıyla)</span><span class="sxs-lookup"><span data-stu-id="adae0-119">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="adae0-120">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="adae0-120">Integrity</span></span>|<span data-ttu-id="adae0-121">Yes</span><span class="sxs-lookup"><span data-stu-id="adae0-121">Yes</span></span>|  
|<span data-ttu-id="adae0-122">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="adae0-122">Confidentiality</span></span>|<span data-ttu-id="adae0-123">Yes</span><span class="sxs-lookup"><span data-stu-id="adae0-123">Yes</span></span>|  
|<span data-ttu-id="adae0-124">Aktarım</span><span class="sxs-lookup"><span data-stu-id="adae0-124">Transport</span></span>|<span data-ttu-id="adae0-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="adae0-125">HTTPS</span></span>|  
|<span data-ttu-id="adae0-126">Bağlama</span><span class="sxs-lookup"><span data-stu-id="adae0-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="adae0-127">Hizmet</span><span class="sxs-lookup"><span data-stu-id="adae0-127">Service</span></span>  
 <span data-ttu-id="adae0-128">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="adae0-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="adae0-129">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="adae0-129">Do one of the following:</span></span>  
  
- <span data-ttu-id="adae0-130">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="adae0-130">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="adae0-131">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="adae0-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="adae0-132">Kod</span><span class="sxs-lookup"><span data-stu-id="adae0-132">Code</span></span>  
 <span data-ttu-id="adae0-133">Aşağıdaki kod, aktarım güvenliği için bir Windows etki alanı Kullanıcı adı ve parolası kullanan bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="adae0-133">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="adae0-134">Hizmetin, istemcinin kimliğini doğrulamak için bir X. 509.440 sertifikası gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="adae0-134">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="adae0-135">Daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="adae0-135">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="adae0-136">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="adae0-136">Configuration</span></span>  
 <span data-ttu-id="adae0-137">Aşağıda, aktarım düzeyi güvenlik ile temel kimlik doğrulaması kullanmak için bir hizmet yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="adae0-137">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="adae0-138">İstemci</span><span class="sxs-lookup"><span data-stu-id="adae0-138">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="adae0-139">Kod</span><span class="sxs-lookup"><span data-stu-id="adae0-139">Code</span></span>  
 <span data-ttu-id="adae0-140">Aşağıdaki kod, Kullanıcı adını ve parolasını içeren istemci kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="adae0-140">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="adae0-141">Kullanıcının geçerli bir Windows Kullanıcı adı ve parolası sağlaması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="adae0-141">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="adae0-142">Kullanıcı adını ve parolayı döndüren kod burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="adae0-142">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="adae0-143">Bilgileri Kullanıcı için sorgulamak üzere bir iletişim kutusu veya başka bir arabirim kullanın.</span><span class="sxs-lookup"><span data-stu-id="adae0-143">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adae0-144">Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="adae0-144">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="adae0-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="adae0-145">Configuration</span></span>  
 <span data-ttu-id="adae0-146">Aşağıdaki kod, istemci yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adae0-146">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adae0-147">Kullanıcı adını ve parolayı ayarlamak için yapılandırma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="adae0-147">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="adae0-148">Burada gösterilen yapılandırma, Kullanıcı adı ve parolasını ayarlamak için kod kullanılarak artıralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="adae0-148">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adae0-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adae0-149">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="adae0-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="adae0-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="adae0-151">Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="adae0-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="adae0-152">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="adae0-152">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="adae0-153">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="adae0-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
