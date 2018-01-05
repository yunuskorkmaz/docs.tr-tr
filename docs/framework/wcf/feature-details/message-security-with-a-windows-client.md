---
title: "Windows İstemcisi ile İleti Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c480706fee27e7023eae5b493b0ca007b4757e97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="022d5-102">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="022d5-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="022d5-103">Bu senaryo gösterilmektedir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci ve sunucu ileti güvenlik modu tarafından güvenli hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="022d5-103">This scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and server secured by message security mode.</span></span> <span data-ttu-id="022d5-104">İstemci ve hizmet Windows kimlik bilgileri kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="022d5-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="022d5-105">![İleti güvenliği Windows İstemcisi ile](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="022d5-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="022d5-106">Özelliği</span><span class="sxs-lookup"><span data-stu-id="022d5-106">Characteristic</span></span>|<span data-ttu-id="022d5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="022d5-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="022d5-108">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="022d5-108">Security Mode</span></span>|<span data-ttu-id="022d5-109">İleti</span><span class="sxs-lookup"><span data-stu-id="022d5-109">Message</span></span>|  
|<span data-ttu-id="022d5-110">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="022d5-110">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="022d5-111">Yalnızca</span><span class="sxs-lookup"><span data-stu-id="022d5-111"> Only</span></span>|  
|<span data-ttu-id="022d5-112">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="022d5-112">Authentication (Server)</span></span>|<span data-ttu-id="022d5-113">İstemci ve sunucu, karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="022d5-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="022d5-114">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="022d5-114">Authentication (Client)</span></span>|<span data-ttu-id="022d5-115">İstemci ve sunucu, karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="022d5-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="022d5-116">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="022d5-116">Integrity</span></span>|<span data-ttu-id="022d5-117">Evet, paylaşılan güvenlik bağlamını kullanarak</span><span class="sxs-lookup"><span data-stu-id="022d5-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="022d5-118">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="022d5-118">Confidentiality</span></span>|<span data-ttu-id="022d5-119">Evet, paylaşılan güvenlik bağlamını kullanarak</span><span class="sxs-lookup"><span data-stu-id="022d5-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="022d5-120">Taşıma</span><span class="sxs-lookup"><span data-stu-id="022d5-120">Transport</span></span>|<span data-ttu-id="022d5-121">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="022d5-121">NET.TCP</span></span>|  
|<span data-ttu-id="022d5-122">Bağlama</span><span class="sxs-lookup"><span data-stu-id="022d5-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="022d5-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="022d5-123">Service</span></span>  
 <span data-ttu-id="022d5-124">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="022d5-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="022d5-125">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="022d5-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="022d5-126">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="022d5-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="022d5-127">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="022d5-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="022d5-128">Kod</span><span class="sxs-lookup"><span data-stu-id="022d5-128">Code</span></span>  
 <span data-ttu-id="022d5-129">Aşağıdaki kod, ileti güvenliği Windows makineyle güvenli içeriği kurmak için kullandığı bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="022d5-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="022d5-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="022d5-130">Configuration</span></span>  
 <span data-ttu-id="022d5-131">Aşağıdaki yapılandırma kodu yerine hizmeti kurmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="022d5-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="022d5-132">İstemci</span><span class="sxs-lookup"><span data-stu-id="022d5-132">Client</span></span>  
 <span data-ttu-id="022d5-133">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="022d5-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="022d5-134">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="022d5-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="022d5-135">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="022d5-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="022d5-136">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="022d5-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="022d5-137">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="022d5-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="022d5-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="022d5-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="022d5-139">Kod</span><span class="sxs-lookup"><span data-stu-id="022d5-139">Code</span></span>  
 <span data-ttu-id="022d5-140">Aşağıdaki kod, bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="022d5-140">The following code creates a client.</span></span> <span data-ttu-id="022d5-141">Bağlama ileti mod güvenliği ve istemci kimlik bilgisi türü ayarlanır `Windows`.</span><span class="sxs-lookup"><span data-stu-id="022d5-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="022d5-142">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="022d5-142">Configuration</span></span>  
 <span data-ttu-id="022d5-143">Aşağıdaki yapılandırma, istemci özelliklerini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="022d5-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="022d5-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="022d5-144">See Also</span></span>  
 [<span data-ttu-id="022d5-145">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="022d5-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="022d5-146">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="022d5-146">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
