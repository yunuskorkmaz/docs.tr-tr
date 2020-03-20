---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184309"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="d0028-102">Windows Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d0028-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="d0028-103">Aşağıdaki senaryo, Windows Security tarafından güvenli bir Windows Communication Foundation (WCF) istemcisi ve hizmetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0028-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="d0028-104">Programlama hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="d0028-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="d0028-105">Bir intranet Web hizmeti insan kaynakları bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0028-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="d0028-106">İstemci bir Windows Form uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d0028-106">The client is a Windows Form application.</span></span> <span data-ttu-id="d0028-107">Uygulama, etki alanını koruyan bir Kerberos denetleyicisi olan bir etki alanında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="d0028-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Windows kimlik doğrulaması ile taşıma güvenliği](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="d0028-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="d0028-109">Characteristic</span></span>|<span data-ttu-id="d0028-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0028-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d0028-111">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="d0028-111">Security Mode</span></span>|<span data-ttu-id="d0028-112">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d0028-112">Transport</span></span>|  
|<span data-ttu-id="d0028-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d0028-113">Interoperability</span></span>|<span data-ttu-id="d0028-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="d0028-114">WCF only</span></span>|  
|<span data-ttu-id="d0028-115">Kimlik Doğrulama (Sunucu)</span><span class="sxs-lookup"><span data-stu-id="d0028-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="d0028-116">Kimlik Doğrulama (İstemci)</span><span class="sxs-lookup"><span data-stu-id="d0028-116">Authentication (Client)</span></span>|<span data-ttu-id="d0028-117">Evet (Windows tümleşik kimlik doğrulamakullanarak)</span><span class="sxs-lookup"><span data-stu-id="d0028-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="d0028-118">Evet (Windows tümleşik kimlik doğrulamakullanarak)</span><span class="sxs-lookup"><span data-stu-id="d0028-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="d0028-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="d0028-119">Integrity</span></span>|<span data-ttu-id="d0028-120">Evet</span><span class="sxs-lookup"><span data-stu-id="d0028-120">Yes</span></span>|  
|<span data-ttu-id="d0028-121">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="d0028-121">Confidentiality</span></span>|<span data-ttu-id="d0028-122">Evet</span><span class="sxs-lookup"><span data-stu-id="d0028-122">Yes</span></span>|  
|<span data-ttu-id="d0028-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d0028-123">Transport</span></span>|<span data-ttu-id="d0028-124">Net. Tcp</span><span class="sxs-lookup"><span data-stu-id="d0028-124">NET.TCP</span></span>|  
|<span data-ttu-id="d0028-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d0028-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d0028-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="d0028-126">Service</span></span>  
 <span data-ttu-id="d0028-127">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="d0028-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d0028-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="d0028-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="d0028-129">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0028-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d0028-130">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="d0028-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d0028-131">Kod</span><span class="sxs-lookup"><span data-stu-id="d0028-131">Code</span></span>  
 <span data-ttu-id="d0028-132">Aşağıdaki kod, Windows güvenliği kullanan bir hizmet bitiş noktasının nasıl oluşturulurunun gösteriş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0028-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="d0028-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0028-133">Configuration</span></span>  
 <span data-ttu-id="d0028-134">Hizmet bitiş noktasını ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d0028-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="d0028-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="d0028-135">Client</span></span>  
 <span data-ttu-id="d0028-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="d0028-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d0028-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="d0028-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="d0028-138">Kodu (ve istemci kodunu) kullanarak tek başına bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0028-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="d0028-139">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0028-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d0028-140">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0028-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d0028-141">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d0028-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d0028-142">Kod</span><span class="sxs-lookup"><span data-stu-id="d0028-142">Code</span></span>  
 <span data-ttu-id="d0028-143">Aşağıdaki kod istemciyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0028-143">The following code creates the client.</span></span> <span data-ttu-id="d0028-144">Bağlama, TCP aktarımını ve istemci kimlik bilgisi türünü Windows'a ayarlı olarak aktarım modu güvenliğini kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d0028-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="d0028-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0028-145">Configuration</span></span>  
 <span data-ttu-id="d0028-146">İstemciyi oluşturmak için kod yerine aşağıdaki yapılandırma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0028-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0028-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0028-147">See also</span></span>

- [<span data-ttu-id="d0028-148">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0028-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="d0028-149">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d0028-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="d0028-150">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d0028-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
