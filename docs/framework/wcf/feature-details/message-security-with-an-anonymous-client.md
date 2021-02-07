---
description: 'Hakkında daha fazla bilgi edinin: anonim bir Istemciyle Ileti güvenliği'
title: Anonim İstemci ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 921ddd9e8e7d2a860f3516c452870bc2bb150911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726981"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="86fb8-103">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="86fb8-103">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="86fb8-104">Aşağıdaki senaryoda, Windows Communication Foundation (WCF) ileti güvenliği ile güvenliği sağlanmış bir istemci ve hizmet gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86fb8-104">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="86fb8-105">Bir tasarım hedefi, aktarım güvenliği yerine ileti güvenliği kullanmak ve ileride daha zengin bir talep tabanlı modeli destekleyebilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86fb8-105">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="86fb8-106">Yetkilendirme için zengin talepler kullanma hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="86fb8-106">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="86fb8-107">Örnek bir uygulama için bkz. [Ileti güvenliği anonim](../samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="86fb8-107">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="86fb8-108">![Anonim bir istemciyle ileti güvenliği](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="86fb8-108">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="86fb8-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="86fb8-109">Characteristic</span></span>|<span data-ttu-id="86fb8-110">Description</span><span class="sxs-lookup"><span data-stu-id="86fb8-110">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="86fb8-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="86fb8-111">Security Mode</span></span>|<span data-ttu-id="86fb8-112">İleti</span><span class="sxs-lookup"><span data-stu-id="86fb8-112">Message</span></span>|
|<span data-ttu-id="86fb8-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="86fb8-113">Interoperability</span></span>|<span data-ttu-id="86fb8-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="86fb8-114">WCF only</span></span>|
|<span data-ttu-id="86fb8-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="86fb8-115">Authentication (Server)</span></span>|<span data-ttu-id="86fb8-116">İlk anlaşma sunucu kimlik doğrulaması gerektirir, ancak istemci kimlik doğrulaması gerektirmez</span><span class="sxs-lookup"><span data-stu-id="86fb8-116">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="86fb8-117">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="86fb8-117">Authentication (Client)</span></span>|<span data-ttu-id="86fb8-118">Yok</span><span class="sxs-lookup"><span data-stu-id="86fb8-118">None</span></span>|
|<span data-ttu-id="86fb8-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="86fb8-119">Integrity</span></span>|<span data-ttu-id="86fb8-120">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="86fb8-120">Yes, using shared security context</span></span>|
|<span data-ttu-id="86fb8-121">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="86fb8-121">Confidentiality</span></span>|<span data-ttu-id="86fb8-122">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="86fb8-122">Yes, using shared security context</span></span>|
|<span data-ttu-id="86fb8-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="86fb8-123">Transport</span></span>|<span data-ttu-id="86fb8-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="86fb8-124">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="86fb8-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="86fb8-125">Service</span></span>

<span data-ttu-id="86fb8-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86fb8-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="86fb8-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="86fb8-127">Do one of the following:</span></span>

- <span data-ttu-id="86fb8-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="86fb8-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="86fb8-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="86fb8-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="86fb8-130">Kod</span><span class="sxs-lookup"><span data-stu-id="86fb8-130">Code</span></span>

<span data-ttu-id="86fb8-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="86fb8-131">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="86fb8-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="86fb8-132">Configuration</span></span>

<span data-ttu-id="86fb8-133">Aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86fb8-133">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="86fb8-134">Hizmet davranışı öğesi, istemciye hizmetin kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86fb8-134">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="86fb8-135">Hizmet öğesi, özniteliğini kullanarak davranışı belirtmelidir `behaviorConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="86fb8-135">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="86fb8-136">Binding öğesi, istemci kimlik bilgisi türünün olduğunu belirtir `None` ve anonim istemcilerin hizmeti kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="86fb8-136">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

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

## <a name="client"></a><span data-ttu-id="86fb8-137">İstemci</span><span class="sxs-lookup"><span data-stu-id="86fb8-137">Client</span></span>

<span data-ttu-id="86fb8-138">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86fb8-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="86fb8-139">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="86fb8-139">Do one of the following:</span></span>

- <span data-ttu-id="86fb8-140">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="86fb8-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="86fb8-141">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="86fb8-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="86fb8-142">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="86fb8-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="86fb8-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="86fb8-143">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="86fb8-144">Kod</span><span class="sxs-lookup"><span data-stu-id="86fb8-144">Code</span></span>

<span data-ttu-id="86fb8-145">Aşağıdaki kod, istemcisinin bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86fb8-145">The following code creates an instance of the client.</span></span> <span data-ttu-id="86fb8-146">Bağlama ileti modu güvenliği kullanır ve istemci kimlik bilgisi türü None olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="86fb8-146">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="86fb8-147">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="86fb8-147">Configuration</span></span>

<span data-ttu-id="86fb8-148">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="86fb8-148">The following code configures the client.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="86fb8-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86fb8-149">See also</span></span>

- [<span data-ttu-id="86fb8-150">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="86fb8-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="86fb8-151">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="86fb8-151">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="86fb8-152">İleti Güvenliği Anonim</span><span class="sxs-lookup"><span data-stu-id="86fb8-152">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="86fb8-153">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="86fb8-153">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="86fb8-154">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="86fb8-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
