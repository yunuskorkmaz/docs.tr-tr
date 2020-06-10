---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 7c83de70e404fe8304bc2e35c1bb5df9e42f95b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576102"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="8d427-102">Temel Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8d427-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="8d427-103">Aşağıdaki çizimde bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d427-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="8d427-104">Sunucu, Güvenli Yuva Katmanı (SSL) için kullanılabilecek geçerli bir X. 509.440 sertifikasına ihtiyaç duyuyor ve istemcilerin sunucunun sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d427-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="8d427-105">Ayrıca, Web hizmeti zaten kullanılabilecek bir SSL uygulamasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8d427-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="8d427-106">Internet Information Services (IIS) üzerinde temel kimlik doğrulamasını etkinleştirme hakkında daha fazla bilgi için bkz <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> ..</span><span class="sxs-lookup"><span data-stu-id="8d427-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Temel kimlik doğrulaması ile taşıma güvenliğini gösteren ekran görüntüsü.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="8d427-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="8d427-108">Characteristic</span></span>|<span data-ttu-id="8d427-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d427-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8d427-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="8d427-110">Security Mode</span></span>|<span data-ttu-id="8d427-111">Aktarım</span><span class="sxs-lookup"><span data-stu-id="8d427-111">Transport</span></span>|  
|<span data-ttu-id="8d427-112">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="8d427-112">Interoperability</span></span>|<span data-ttu-id="8d427-113">Mevcut Web hizmeti istemcileri ve hizmetleriyle</span><span class="sxs-lookup"><span data-stu-id="8d427-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="8d427-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="8d427-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="8d427-115">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="8d427-115">Authentication (Client)</span></span>|<span data-ttu-id="8d427-116">Evet (HTTPS kullanarak)</span><span class="sxs-lookup"><span data-stu-id="8d427-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="8d427-117">Evet (Kullanıcı adı/parola aracılığıyla)</span><span class="sxs-lookup"><span data-stu-id="8d427-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="8d427-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="8d427-118">Integrity</span></span>|<span data-ttu-id="8d427-119">Yes</span><span class="sxs-lookup"><span data-stu-id="8d427-119">Yes</span></span>|  
|<span data-ttu-id="8d427-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="8d427-120">Confidentiality</span></span>|<span data-ttu-id="8d427-121">Yes</span><span class="sxs-lookup"><span data-stu-id="8d427-121">Yes</span></span>|  
|<span data-ttu-id="8d427-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="8d427-122">Transport</span></span>|<span data-ttu-id="8d427-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="8d427-123">HTTPS</span></span>|  
|<span data-ttu-id="8d427-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="8d427-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8d427-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="8d427-125">Service</span></span>  
 <span data-ttu-id="8d427-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8d427-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8d427-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="8d427-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="8d427-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8d427-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="8d427-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="8d427-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8d427-130">Kod</span><span class="sxs-lookup"><span data-stu-id="8d427-130">Code</span></span>  
 <span data-ttu-id="8d427-131">Aşağıdaki kod, aktarım güvenliği için bir Windows etki alanı Kullanıcı adı ve parolası kullanan bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d427-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="8d427-132">Hizmetin, istemcinin kimliğini doğrulamak için bir X. 509.440 sertifikası gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d427-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="8d427-133">Daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8d427-133">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="8d427-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d427-134">Configuration</span></span>  
 <span data-ttu-id="8d427-135">Aşağıda, aktarım düzeyi güvenlik ile temel kimlik doğrulaması kullanmak için bir hizmet yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="8d427-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="8d427-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="8d427-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="8d427-137">Kod</span><span class="sxs-lookup"><span data-stu-id="8d427-137">Code</span></span>  
 <span data-ttu-id="8d427-138">Aşağıdaki kod, Kullanıcı adını ve parolasını içeren istemci kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d427-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="8d427-139">Kullanıcının geçerli bir Windows Kullanıcı adı ve parolası sağlaması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d427-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="8d427-140">Kullanıcı adını ve parolayı döndüren kod burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="8d427-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="8d427-141">Bilgileri Kullanıcı için sorgulamak üzere bir iletişim kutusu veya başka bir arabirim kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d427-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d427-142">Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d427-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="8d427-143">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d427-143">Configuration</span></span>  
 <span data-ttu-id="8d427-144">Aşağıdaki kod, istemci yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d427-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d427-145">Kullanıcı adını ve parolayı ayarlamak için yapılandırma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8d427-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="8d427-146">Burada gösterilen yapılandırma, Kullanıcı adı ve parolasını ayarlamak için kod kullanılarak artıralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d427-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d427-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d427-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="8d427-148">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="8d427-148">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="8d427-149">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d427-149">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="8d427-150">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="8d427-150">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="8d427-151">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8d427-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
