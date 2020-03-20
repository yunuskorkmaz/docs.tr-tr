---
title: Windows İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: bcfeb5f863b1dd6cf9171a7fc53c8984ea68ecb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184624"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="6f641-102">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6f641-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="6f641-103">Bu senaryo, ileti güvenliği modu tarafından güvenli bir Windows Communication Foundation (WCF) istemcisi ve sunucusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f641-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="6f641-104">İstemci ve hizmet, Windows kimlik bilgileri kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6f641-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="6f641-105">![Windows istemcisi ile ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="6f641-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="6f641-106">Özellik</span><span class="sxs-lookup"><span data-stu-id="6f641-106">Characteristic</span></span>|<span data-ttu-id="6f641-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f641-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6f641-108">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="6f641-108">Security Mode</span></span>|<span data-ttu-id="6f641-109">İleti</span><span class="sxs-lookup"><span data-stu-id="6f641-109">Message</span></span>|  
|<span data-ttu-id="6f641-110">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="6f641-110">Interoperability</span></span>|<span data-ttu-id="6f641-111">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="6f641-111">WCF Only</span></span>|  
|<span data-ttu-id="6f641-112">Kimlik Doğrulama (Sunucu)</span><span class="sxs-lookup"><span data-stu-id="6f641-112">Authentication (Server)</span></span>|<span data-ttu-id="6f641-113">Sunucu nun ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6f641-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="6f641-114">Kimlik Doğrulama (İstemci)</span><span class="sxs-lookup"><span data-stu-id="6f641-114">Authentication (Client)</span></span>|<span data-ttu-id="6f641-115">Sunucu nun ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6f641-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="6f641-116">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="6f641-116">Integrity</span></span>|<span data-ttu-id="6f641-117">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="6f641-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="6f641-118">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="6f641-118">Confidentiality</span></span>|<span data-ttu-id="6f641-119">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="6f641-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="6f641-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6f641-120">Transport</span></span>|<span data-ttu-id="6f641-121">Net. Tcp</span><span class="sxs-lookup"><span data-stu-id="6f641-121">NET.TCP</span></span>|  
|<span data-ttu-id="6f641-122">Bağlama</span><span class="sxs-lookup"><span data-stu-id="6f641-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="6f641-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="6f641-123">Service</span></span>  
 <span data-ttu-id="6f641-124">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="6f641-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6f641-125">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="6f641-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="6f641-126">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f641-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="6f641-127">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="6f641-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f641-128">Kod</span><span class="sxs-lookup"><span data-stu-id="6f641-128">Code</span></span>  
 <span data-ttu-id="6f641-129">Aşağıdaki kod, windows makinesiyle güvenli bir bağlam oluşturmak için ileti güvenliğini kullanan bir hizmet bitiş noktasının nasıl oluşturultur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f641-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="6f641-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f641-130">Configuration</span></span>  
 <span data-ttu-id="6f641-131">Hizmeti ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="6f641-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="6f641-132">İstemci</span><span class="sxs-lookup"><span data-stu-id="6f641-132">Client</span></span>  
 <span data-ttu-id="6f641-133">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="6f641-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6f641-134">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="6f641-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="6f641-135">Kodu (ve istemci kodunu) kullanarak tek başına bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f641-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="6f641-136">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f641-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="6f641-137">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f641-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="6f641-138">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6f641-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="6f641-139">Kod</span><span class="sxs-lookup"><span data-stu-id="6f641-139">Code</span></span>  
 <span data-ttu-id="6f641-140">Aşağıdaki kod bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f641-140">The following code creates a client.</span></span> <span data-ttu-id="6f641-141">Bağlama İleti modu güvenliği için ve istemci kimlik bilgisi türü `Windows`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6f641-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="6f641-142">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f641-142">Configuration</span></span>  
 <span data-ttu-id="6f641-143">İstemci özelliklerini ayarlamak için aşağıdaki yapılandırma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f641-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f641-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f641-144">See also</span></span>

- [<span data-ttu-id="6f641-145">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f641-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="6f641-146">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6f641-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
