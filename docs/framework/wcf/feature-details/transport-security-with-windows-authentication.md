---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
description: Windows güvenliği tarafından güvenliği sağlanmış bir WCF istemcisi/hizmeti gösteren bu senaryoyu inceleyin. Bu örnekte, bir intranet hizmeti insan kaynakları bilgilerini görüntüler.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 9b81f2f2fb6352af254146951ed35ad4fdca8caa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545213"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="e5a4d-104">Windows Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e5a4d-104">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="e5a4d-105">Aşağıdaki senaryoda Windows güvenliği tarafından güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-105">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="e5a4d-106">Programlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows kimlik bilgileriyle hizmeti güvenli hale getirme](../how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="e5a4d-106">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="e5a4d-107">Bir intranet Web hizmeti insan kaynakları bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-107">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="e5a4d-108">İstemci bir Windows form uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-108">The client is a Windows Form application.</span></span> <span data-ttu-id="e5a4d-109">Uygulama, etki alanının güvenliğini sağlamak üzere Kerberos denetleyicisi olan bir etki alanına dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-109">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Windows kimlik doğrulama ile aktarım güvenliği](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="e5a4d-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="e5a4d-111">Characteristic</span></span>|<span data-ttu-id="e5a4d-112">Description</span><span class="sxs-lookup"><span data-stu-id="e5a4d-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e5a4d-113">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="e5a4d-113">Security Mode</span></span>|<span data-ttu-id="e5a4d-114">Aktarım</span><span class="sxs-lookup"><span data-stu-id="e5a4d-114">Transport</span></span>|  
|<span data-ttu-id="e5a4d-115">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e5a4d-115">Interoperability</span></span>|<span data-ttu-id="e5a4d-116">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="e5a4d-116">WCF only</span></span>|  
|<span data-ttu-id="e5a4d-117">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="e5a4d-117">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="e5a4d-118">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="e5a4d-118">Authentication (Client)</span></span>|<span data-ttu-id="e5a4d-119">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="e5a4d-119">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="e5a4d-120">Evet (Windows tümleşik kimlik doğrulaması kullanarak)</span><span class="sxs-lookup"><span data-stu-id="e5a4d-120">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="e5a4d-121">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="e5a4d-121">Integrity</span></span>|<span data-ttu-id="e5a4d-122">Yes</span><span class="sxs-lookup"><span data-stu-id="e5a4d-122">Yes</span></span>|  
|<span data-ttu-id="e5a4d-123">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="e5a4d-123">Confidentiality</span></span>|<span data-ttu-id="e5a4d-124">Yes</span><span class="sxs-lookup"><span data-stu-id="e5a4d-124">Yes</span></span>|  
|<span data-ttu-id="e5a4d-125">Aktarım</span><span class="sxs-lookup"><span data-stu-id="e5a4d-125">Transport</span></span>|<span data-ttu-id="e5a4d-126">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="e5a4d-126">NET.TCP</span></span>|  
|<span data-ttu-id="e5a4d-127">Bağlama</span><span class="sxs-lookup"><span data-stu-id="e5a4d-127">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="e5a4d-128">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e5a4d-128">Service</span></span>  
 <span data-ttu-id="e5a4d-129">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e5a4d-130">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e5a4d-130">Do one of the following:</span></span>  
  
- <span data-ttu-id="e5a4d-131">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="e5a4d-132">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e5a4d-133">Kod</span><span class="sxs-lookup"><span data-stu-id="e5a4d-133">Code</span></span>  
 <span data-ttu-id="e5a4d-134">Aşağıdaki kod, Windows güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-134">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="e5a4d-135">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e5a4d-135">Configuration</span></span>  
 <span data-ttu-id="e5a4d-136">Hizmet uç noktasını ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e5a4d-136">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="e5a4d-137">İstemci</span><span class="sxs-lookup"><span data-stu-id="e5a4d-137">Client</span></span>  
 <span data-ttu-id="e5a4d-138">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e5a4d-139">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e5a4d-139">Do one of the following:</span></span>  
  
- <span data-ttu-id="e5a4d-140">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="e5a4d-140">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="e5a4d-141">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e5a4d-142">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e5a4d-143">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e5a4d-143">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="e5a4d-144">Kod</span><span class="sxs-lookup"><span data-stu-id="e5a4d-144">Code</span></span>  
 <span data-ttu-id="e5a4d-145">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-145">The following code creates the client.</span></span> <span data-ttu-id="e5a4d-146">Bağlama, istemci kimlik bilgisi türü Windows olarak ayarlanmış şekilde TCP aktarımından aktarım modu güvenliğini kullanacak şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-146">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="e5a4d-147">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e5a4d-147">Configuration</span></span>  
 <span data-ttu-id="e5a4d-148">Aşağıdaki yapılandırma, istemci oluşturmak için kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-148">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5a4d-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a4d-149">See also</span></span>

- [<span data-ttu-id="e5a4d-150">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="e5a4d-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="e5a4d-151">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e5a4d-151">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="e5a4d-152">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e5a4d-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
