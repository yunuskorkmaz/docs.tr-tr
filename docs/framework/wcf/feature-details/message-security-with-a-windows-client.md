---
title: Windows İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: dcb311523c6ec41b62f6e69fe6bc7635b9d49708
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595238"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="f33e8-102">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f33e8-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="f33e8-103">Bu senaryoda ileti güvenliği modu tarafından güvenli hale getirilmiş bir Windows Communication Foundation (WCF) istemci ve sunucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f33e8-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="f33e8-104">İstemci ve hizmet, Windows kimlik bilgileri kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="f33e8-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="f33e8-105">![Windows istemcisi ile ileti güvenliği](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="f33e8-105">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="f33e8-106">Özellik</span><span class="sxs-lookup"><span data-stu-id="f33e8-106">Characteristic</span></span>|<span data-ttu-id="f33e8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f33e8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f33e8-108">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="f33e8-108">Security Mode</span></span>|<span data-ttu-id="f33e8-109">İleti</span><span class="sxs-lookup"><span data-stu-id="f33e8-109">Message</span></span>|  
|<span data-ttu-id="f33e8-110">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f33e8-110">Interoperability</span></span>|<span data-ttu-id="f33e8-111">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="f33e8-111">WCF Only</span></span>|  
|<span data-ttu-id="f33e8-112">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="f33e8-112">Authentication (Server)</span></span>|<span data-ttu-id="f33e8-113">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f33e8-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="f33e8-114">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="f33e8-114">Authentication (Client)</span></span>|<span data-ttu-id="f33e8-115">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f33e8-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="f33e8-116">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="f33e8-116">Integrity</span></span>|<span data-ttu-id="f33e8-117">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="f33e8-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="f33e8-118">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="f33e8-118">Confidentiality</span></span>|<span data-ttu-id="f33e8-119">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="f33e8-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="f33e8-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="f33e8-120">Transport</span></span>|<span data-ttu-id="f33e8-121">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="f33e8-121">NET.TCP</span></span>|  
|<span data-ttu-id="f33e8-122">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f33e8-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f33e8-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="f33e8-123">Service</span></span>  
 <span data-ttu-id="f33e8-124">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f33e8-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f33e8-125">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="f33e8-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="f33e8-126">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f33e8-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="f33e8-127">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f33e8-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f33e8-128">Kod</span><span class="sxs-lookup"><span data-stu-id="f33e8-128">Code</span></span>  
 <span data-ttu-id="f33e8-129">Aşağıdaki kod, bir Windows makinesiyle güvenli bir bağlam oluşturmak için ileti güvenliği kullanan bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f33e8-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="f33e8-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f33e8-130">Configuration</span></span>  
 <span data-ttu-id="f33e8-131">Hizmeti ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f33e8-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f33e8-132">İstemci</span><span class="sxs-lookup"><span data-stu-id="f33e8-132">Client</span></span>  
 <span data-ttu-id="f33e8-133">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f33e8-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f33e8-134">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="f33e8-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="f33e8-135">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="f33e8-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="f33e8-136">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f33e8-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="f33e8-137">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f33e8-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="f33e8-138">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f33e8-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="f33e8-139">Kod</span><span class="sxs-lookup"><span data-stu-id="f33e8-139">Code</span></span>  
 <span data-ttu-id="f33e8-140">Aşağıdaki kod bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f33e8-140">The following code creates a client.</span></span> <span data-ttu-id="f33e8-141">Bağlama Ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `Windows` .</span><span class="sxs-lookup"><span data-stu-id="f33e8-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="f33e8-142">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f33e8-142">Configuration</span></span>  
 <span data-ttu-id="f33e8-143">İstemci özelliklerini ayarlamak için aşağıdaki yapılandırma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f33e8-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f33e8-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f33e8-144">See also</span></span>

- [<span data-ttu-id="f33e8-145">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="f33e8-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="f33e8-146">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f33e8-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
