---
description: 'Hakkında daha fazla bilgi edinin: Windows Istemcisiyle Ileti güvenliği'
title: Windows İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: 97d415f68b4374ab2b18360347d7753f6be51313
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756103"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="b0cad-103">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b0cad-103">Message Security with a Windows Client</span></span>

<span data-ttu-id="b0cad-104">Bu senaryoda ileti güvenliği modu tarafından güvenli hale getirilmiş bir Windows Communication Foundation (WCF) istemci ve sunucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0cad-104">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="b0cad-105">İstemci ve hizmet, Windows kimlik bilgileri kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="b0cad-105">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="b0cad-106">![Windows istemcisi ile ileti güvenliği](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="b0cad-106">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="b0cad-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="b0cad-107">Characteristic</span></span>|<span data-ttu-id="b0cad-108">Description</span><span class="sxs-lookup"><span data-stu-id="b0cad-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b0cad-109">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="b0cad-109">Security Mode</span></span>|<span data-ttu-id="b0cad-110">İleti</span><span class="sxs-lookup"><span data-stu-id="b0cad-110">Message</span></span>|  
|<span data-ttu-id="b0cad-111">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="b0cad-111">Interoperability</span></span>|<span data-ttu-id="b0cad-112">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="b0cad-112">WCF Only</span></span>|  
|<span data-ttu-id="b0cad-113">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="b0cad-113">Authentication (Server)</span></span>|<span data-ttu-id="b0cad-114">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b0cad-114">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="b0cad-115">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="b0cad-115">Authentication (Client)</span></span>|<span data-ttu-id="b0cad-116">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b0cad-116">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="b0cad-117">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="b0cad-117">Integrity</span></span>|<span data-ttu-id="b0cad-118">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="b0cad-118">Yes, using shared security context</span></span>|  
|<span data-ttu-id="b0cad-119">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="b0cad-119">Confidentiality</span></span>|<span data-ttu-id="b0cad-120">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="b0cad-120">Yes, using shared security context</span></span>|  
|<span data-ttu-id="b0cad-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="b0cad-121">Transport</span></span>|<span data-ttu-id="b0cad-122">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="b0cad-122">NET.TCP</span></span>|  
|<span data-ttu-id="b0cad-123">Bağlama</span><span class="sxs-lookup"><span data-stu-id="b0cad-123">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="b0cad-124">Hizmet</span><span class="sxs-lookup"><span data-stu-id="b0cad-124">Service</span></span>  

 <span data-ttu-id="b0cad-125">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0cad-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b0cad-126">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="b0cad-126">Do one of the following:</span></span>  
  
- <span data-ttu-id="b0cad-127">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0cad-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b0cad-128">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b0cad-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0cad-129">Kod</span><span class="sxs-lookup"><span data-stu-id="b0cad-129">Code</span></span>  

 <span data-ttu-id="b0cad-130">Aşağıdaki kod, bir Windows makinesiyle güvenli bir bağlam oluşturmak için ileti güvenliği kullanan bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0cad-130">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="b0cad-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0cad-131">Configuration</span></span>  

 <span data-ttu-id="b0cad-132">Hizmeti ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b0cad-132">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="b0cad-133">İstemci</span><span class="sxs-lookup"><span data-stu-id="b0cad-133">Client</span></span>  

 <span data-ttu-id="b0cad-134">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0cad-134">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b0cad-135">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="b0cad-135">Do one of the following:</span></span>  
  
- <span data-ttu-id="b0cad-136">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="b0cad-136">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="b0cad-137">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0cad-137">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b0cad-138">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0cad-138">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b0cad-139">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0cad-139">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b0cad-140">Kod</span><span class="sxs-lookup"><span data-stu-id="b0cad-140">Code</span></span>  

 <span data-ttu-id="b0cad-141">Aşağıdaki kod bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0cad-141">The following code creates a client.</span></span> <span data-ttu-id="b0cad-142">Bağlama Ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `Windows` .</span><span class="sxs-lookup"><span data-stu-id="b0cad-142">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="b0cad-143">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0cad-143">Configuration</span></span>  

 <span data-ttu-id="b0cad-144">İstemci özelliklerini ayarlamak için aşağıdaki yapılandırma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0cad-144">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0cad-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0cad-145">See also</span></span>

- [<span data-ttu-id="b0cad-146">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="b0cad-146">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b0cad-147">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b0cad-147">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
