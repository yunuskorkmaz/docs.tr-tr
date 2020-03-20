---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 1b2b451eb1ea6a1a49ce1ba8cc1edef1fe72d01b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184348"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="979c4-102">Temel Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="979c4-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="979c4-103">Aşağıdaki resimde bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="979c4-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="979c4-104">Sunucunun Güvenli Soket katmanı (SSL) için kullanılabilecek geçerli bir X.509 sertifikasına ihtiyacı vardır ve istemcilerin sunucunun sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="979c4-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="979c4-105">Ayrıca, Web hizmeti zaten kullanılabilecek bir SSL uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="979c4-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="979c4-106">Internet Bilgi Hizmetleri 'nde (IIS) temel kimlik <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>doğrulamayı etkinleştirme hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="979c4-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Temel kimlik doğrulaması ile aktarım güvenliğini gösteren ekran görüntüsü.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="979c4-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="979c4-108">Characteristic</span></span>|<span data-ttu-id="979c4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="979c4-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="979c4-110">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="979c4-110">Security Mode</span></span>|<span data-ttu-id="979c4-111">Aktarım</span><span class="sxs-lookup"><span data-stu-id="979c4-111">Transport</span></span>|  
|<span data-ttu-id="979c4-112">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="979c4-112">Interoperability</span></span>|<span data-ttu-id="979c4-113">Mevcut Web hizmeti istemcileri ve hizmetleri ile</span><span class="sxs-lookup"><span data-stu-id="979c4-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="979c4-114">Kimlik Doğrulama (Sunucu)</span><span class="sxs-lookup"><span data-stu-id="979c4-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="979c4-115">Kimlik Doğrulama (İstemci)</span><span class="sxs-lookup"><span data-stu-id="979c4-115">Authentication (Client)</span></span>|<span data-ttu-id="979c4-116">Evet (HTTPS kullanarak)</span><span class="sxs-lookup"><span data-stu-id="979c4-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="979c4-117">Evet (Kullanıcı adı/Şifre ile)</span><span class="sxs-lookup"><span data-stu-id="979c4-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="979c4-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="979c4-118">Integrity</span></span>|<span data-ttu-id="979c4-119">Evet</span><span class="sxs-lookup"><span data-stu-id="979c4-119">Yes</span></span>|  
|<span data-ttu-id="979c4-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="979c4-120">Confidentiality</span></span>|<span data-ttu-id="979c4-121">Evet</span><span class="sxs-lookup"><span data-stu-id="979c4-121">Yes</span></span>|  
|<span data-ttu-id="979c4-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="979c4-122">Transport</span></span>|<span data-ttu-id="979c4-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="979c4-123">HTTPS</span></span>|  
|<span data-ttu-id="979c4-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="979c4-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="979c4-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="979c4-125">Service</span></span>  
 <span data-ttu-id="979c4-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="979c4-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="979c4-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="979c4-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="979c4-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="979c4-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="979c4-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="979c4-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="979c4-130">Kod</span><span class="sxs-lookup"><span data-stu-id="979c4-130">Code</span></span>  
 <span data-ttu-id="979c4-131">Aşağıdaki kod, aktarım güvenliği için Windows etki alanı kullanıcı adı ve parolasını kullanan bir hizmet bitiş noktasının nasıl oluşturulurunun gösteriş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="979c4-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="979c4-132">Hizmetin istemciye kimlik doğrulaması için X.509 sertifikası gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="979c4-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="979c4-133">Daha fazla bilgi için bkz: [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [Nasıl Yapılacağını: SSL Sertifikası olan bir Bağlantı Noktasını Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)</span><span class="sxs-lookup"><span data-stu-id="979c4-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="979c4-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="979c4-134">Configuration</span></span>  
 <span data-ttu-id="979c4-135">Aşağıdaki, bir hizmeti aktarım düzeyinde güvenlikle temel kimlik doğrulamasını kullanacak şekilde yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="979c4-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="979c4-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="979c4-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="979c4-137">Kod</span><span class="sxs-lookup"><span data-stu-id="979c4-137">Code</span></span>  
 <span data-ttu-id="979c4-138">Aşağıdaki kod, kullanıcı adı ve parolayı içeren istemci kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="979c4-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="979c4-139">Kullanıcının geçerli bir Windows kullanıcı adı ve parola sağlaması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="979c4-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="979c4-140">Kullanıcı adını ve parolayı döndürecek kod burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="979c4-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="979c4-141">Bilgileri kullanıcıyı sorgulamak için bir iletişim kutusu veya başka bir arabirim kullanın.</span><span class="sxs-lookup"><span data-stu-id="979c4-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="979c4-142">Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="979c4-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="979c4-143">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="979c4-143">Configuration</span></span>  
 <span data-ttu-id="979c4-144">Aşağıdaki kod istemci yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="979c4-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="979c4-145">Kullanıcı adını ve parolayı ayarlamak için yapılandırmayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="979c4-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="979c4-146">Burada gösterilen yapılandırma, kullanıcı adını ve parolayı ayarlamak için kod kullanılarak artırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="979c4-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="979c4-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="979c4-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="979c4-148">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="979c4-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="979c4-149">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="979c4-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="979c4-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="979c4-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="979c4-151">\<istemciKimlik bilgileri></span><span class="sxs-lookup"><span data-stu-id="979c4-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="979c4-152">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="979c4-152">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
