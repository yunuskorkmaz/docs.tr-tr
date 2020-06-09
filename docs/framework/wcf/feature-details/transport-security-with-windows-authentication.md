---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 6703da4f97cba38ee0dc334d3010ca509d1fb3ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598703"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="06739-102">Windows Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="06739-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="06739-103">Aşağıdaki senaryoda Windows güvenliği tarafından güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="06739-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="06739-104">Programlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows kimlik bilgileriyle hizmeti güvenli hale getirme](../how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="06739-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="06739-105">Bir intranet Web hizmeti insan kaynakları bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="06739-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="06739-106">İstemci bir Windows form uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="06739-106">The client is a Windows Form application.</span></span> <span data-ttu-id="06739-107">Uygulama, etki alanının güvenliğini sağlamak üzere Kerberos denetleyicisi olan bir etki alanına dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="06739-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Windows kimlik doğrulama ile aktarım güvenliği](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="06739-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="06739-109">Characteristic</span></span>|<span data-ttu-id="06739-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06739-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="06739-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="06739-111">Security Mode</span></span>|<span data-ttu-id="06739-112">Aktarım</span><span class="sxs-lookup"><span data-stu-id="06739-112">Transport</span></span>|  
|<span data-ttu-id="06739-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="06739-113">Interoperability</span></span>|<span data-ttu-id="06739-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="06739-114">WCF only</span></span>|  
|<span data-ttu-id="06739-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="06739-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="06739-116">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="06739-116">Authentication (Client)</span></span>|<span data-ttu-id="06739-117">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="06739-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="06739-118">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="06739-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="06739-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="06739-119">Integrity</span></span>|<span data-ttu-id="06739-120">Yes</span><span class="sxs-lookup"><span data-stu-id="06739-120">Yes</span></span>|  
|<span data-ttu-id="06739-121">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="06739-121">Confidentiality</span></span>|<span data-ttu-id="06739-122">Yes</span><span class="sxs-lookup"><span data-stu-id="06739-122">Yes</span></span>|  
|<span data-ttu-id="06739-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="06739-123">Transport</span></span>|<span data-ttu-id="06739-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="06739-124">NET.TCP</span></span>|  
|<span data-ttu-id="06739-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="06739-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="06739-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="06739-126">Service</span></span>  
 <span data-ttu-id="06739-127">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="06739-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="06739-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="06739-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="06739-129">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06739-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="06739-130">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="06739-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="06739-131">Kod</span><span class="sxs-lookup"><span data-stu-id="06739-131">Code</span></span>  
 <span data-ttu-id="06739-132">Aşağıdaki kod, Windows güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="06739-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="06739-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="06739-133">Configuration</span></span>  
 <span data-ttu-id="06739-134">Hizmet uç noktasını ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="06739-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="06739-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="06739-135">Client</span></span>  
 <span data-ttu-id="06739-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="06739-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="06739-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="06739-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="06739-138">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="06739-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="06739-139">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06739-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="06739-140">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="06739-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="06739-141">Örnek:</span><span class="sxs-lookup"><span data-stu-id="06739-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="06739-142">Kod</span><span class="sxs-lookup"><span data-stu-id="06739-142">Code</span></span>  
 <span data-ttu-id="06739-143">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06739-143">The following code creates the client.</span></span> <span data-ttu-id="06739-144">Bağlama, istemci kimlik bilgisi türü Windows olarak ayarlanmış şekilde TCP aktarımından aktarım modu güvenliğini kullanacak şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="06739-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="06739-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="06739-145">Configuration</span></span>  
 <span data-ttu-id="06739-146">Aşağıdaki yapılandırma, istemci oluşturmak için kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06739-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06739-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06739-147">See also</span></span>

- [<span data-ttu-id="06739-148">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="06739-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="06739-149">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="06739-149">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="06739-150">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="06739-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
