---
title: Anonim İstemci ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: aed56be359f094db483ab1d012bd77a1096433b6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553772"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="5ac46-102">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5ac46-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="5ac46-103">Aşağıdaki senaryoda, Windows Communication Foundation (WCF) ileti güvenliği ile güvenliği sağlanmış bir istemci ve hizmet gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ac46-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="5ac46-104">Bir tasarım hedefi, aktarım güvenliği yerine ileti güvenliği kullanmak ve ileride daha zengin bir talep tabanlı modeli destekleyebilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ac46-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="5ac46-105">Yetkilendirme için zengin talepler kullanma hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="5ac46-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="5ac46-106">Örnek bir uygulama için bkz. [Ileti güvenliği anonim](../samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="5ac46-106">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="5ac46-107">![Anonim bir istemciyle ileti güvenliği](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="5ac46-107">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="5ac46-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ac46-108">Characteristic</span></span>|<span data-ttu-id="5ac46-109">Description</span><span class="sxs-lookup"><span data-stu-id="5ac46-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="5ac46-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="5ac46-110">Security Mode</span></span>|<span data-ttu-id="5ac46-111">İleti</span><span class="sxs-lookup"><span data-stu-id="5ac46-111">Message</span></span>|
|<span data-ttu-id="5ac46-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="5ac46-112">Interoperability</span></span>|<span data-ttu-id="5ac46-113">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="5ac46-113">WCF only</span></span>|
|<span data-ttu-id="5ac46-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="5ac46-114">Authentication (Server)</span></span>|<span data-ttu-id="5ac46-115">İlk anlaşma sunucu kimlik doğrulaması gerektirir, ancak istemci kimlik doğrulaması gerektirmez</span><span class="sxs-lookup"><span data-stu-id="5ac46-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="5ac46-116">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="5ac46-116">Authentication (Client)</span></span>|<span data-ttu-id="5ac46-117">Yok</span><span class="sxs-lookup"><span data-stu-id="5ac46-117">None</span></span>|
|<span data-ttu-id="5ac46-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="5ac46-118">Integrity</span></span>|<span data-ttu-id="5ac46-119">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="5ac46-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="5ac46-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="5ac46-120">Confidentiality</span></span>|<span data-ttu-id="5ac46-121">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="5ac46-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="5ac46-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="5ac46-122">Transport</span></span>|<span data-ttu-id="5ac46-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="5ac46-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="5ac46-124">Hizmet</span><span class="sxs-lookup"><span data-stu-id="5ac46-124">Service</span></span>

<span data-ttu-id="5ac46-125">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5ac46-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5ac46-126">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="5ac46-126">Do one of the following:</span></span>

- <span data-ttu-id="5ac46-127">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5ac46-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="5ac46-128">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5ac46-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="5ac46-129">Kod</span><span class="sxs-lookup"><span data-stu-id="5ac46-129">Code</span></span>

<span data-ttu-id="5ac46-130">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5ac46-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="5ac46-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ac46-131">Configuration</span></span>

<span data-ttu-id="5ac46-132">Aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac46-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="5ac46-133">Hizmet davranışı öğesi, istemciye hizmetin kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ac46-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="5ac46-134">Hizmet öğesi, özniteliğini kullanarak davranışı belirtmelidir `behaviorConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5ac46-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="5ac46-135">Binding öğesi, istemci kimlik bilgisi türünün olduğunu belirtir `None` ve anonim istemcilerin hizmeti kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5ac46-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="5ac46-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="5ac46-136">Client</span></span>

<span data-ttu-id="5ac46-137">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5ac46-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5ac46-138">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="5ac46-138">Do one of the following:</span></span>

- <span data-ttu-id="5ac46-139">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="5ac46-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="5ac46-140">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5ac46-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5ac46-141">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5ac46-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5ac46-142">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5ac46-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="5ac46-143">Kod</span><span class="sxs-lookup"><span data-stu-id="5ac46-143">Code</span></span>

<span data-ttu-id="5ac46-144">Aşağıdaki kod, istemcisinin bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ac46-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="5ac46-145">Bağlama ileti modu güvenliği kullanır ve istemci kimlik bilgisi türü None olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5ac46-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="5ac46-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ac46-146">Configuration</span></span>

<span data-ttu-id="5ac46-147">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ac46-147">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5ac46-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac46-148">See also</span></span>

- [<span data-ttu-id="5ac46-149">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="5ac46-149">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="5ac46-150">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5ac46-150">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="5ac46-151">İleti Güvenliği Anonim</span><span class="sxs-lookup"><span data-stu-id="5ac46-151">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="5ac46-152">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="5ac46-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="5ac46-153">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5ac46-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
