---
title: Anonim İstemci ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 613b85e18109faa2a4386090e91aaddcfd8e0b68
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680315"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="dd858-102">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="dd858-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="dd858-103">Aşağıdaki senaryoda bir istemci ve Windows Communication Foundation (WCF) ileti güvenliği tarafından güvenliği sağlanan hizmet gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd858-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="dd858-104">Gelecekte daha zengin bir beyana dayalı modeli destekleyebilir böylece tasarım hedefi aktarım güvenliği yerine ileti güvenliği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="dd858-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="dd858-105">Yetkilendirme için zengin talep kullanma hakkında daha fazla bilgi için bkz. [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="dd858-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="dd858-106">Örnek bir uygulama için bkz: [ileti güvenliği anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="dd858-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="dd858-107">![İleti güvenliği anonim istemci ile](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="dd858-107">![Message security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="dd858-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="dd858-108">Characteristic</span></span>|<span data-ttu-id="dd858-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd858-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="dd858-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="dd858-110">Security Mode</span></span>|<span data-ttu-id="dd858-111">İleti</span><span class="sxs-lookup"><span data-stu-id="dd858-111">Message</span></span>|
|<span data-ttu-id="dd858-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="dd858-112">Interoperability</span></span>|<span data-ttu-id="dd858-113">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="dd858-113">WCF only</span></span>|
|<span data-ttu-id="dd858-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="dd858-114">Authentication (Server)</span></span>|<span data-ttu-id="dd858-115">İlk anlaşma sunucu kimlik doğrulaması, ancak değil istemci kimlik doğrulaması gerektirir</span><span class="sxs-lookup"><span data-stu-id="dd858-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="dd858-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="dd858-116">Authentication (Client)</span></span>|<span data-ttu-id="dd858-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="dd858-117">None</span></span>|
|<span data-ttu-id="dd858-118">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="dd858-118">Integrity</span></span>|<span data-ttu-id="dd858-119">Evet, paylaşılan bir güvenlik bağlamı kullanma</span><span class="sxs-lookup"><span data-stu-id="dd858-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="dd858-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="dd858-120">Confidentiality</span></span>|<span data-ttu-id="dd858-121">Evet, paylaşılan bir güvenlik bağlamı kullanma</span><span class="sxs-lookup"><span data-stu-id="dd858-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="dd858-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="dd858-122">Transport</span></span>|<span data-ttu-id="dd858-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="dd858-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="dd858-124">Hizmet</span><span class="sxs-lookup"><span data-stu-id="dd858-124">Service</span></span>

<span data-ttu-id="dd858-125">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="dd858-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="dd858-126">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="dd858-126">Do one of the following:</span></span>

- <span data-ttu-id="dd858-127">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd858-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="dd858-128">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="dd858-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="dd858-129">Kod</span><span class="sxs-lookup"><span data-stu-id="dd858-129">Code</span></span>

<span data-ttu-id="dd858-130">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd858-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="dd858-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd858-131">Configuration</span></span>

<span data-ttu-id="dd858-132">Aşağıdaki yapılandırmayı kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd858-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="dd858-133">Hizmet davranışı öğesi hizmete istemcinin kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd858-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="dd858-134">Hizmet öğesi davranışını kullanarak belirtmelisiniz `behaviorConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dd858-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="dd858-135">İstemci kimlik bilgisi türü olduğunu bağlama öğesi belirtir `None`, hizmeti kullanmak anonim istemcilere izin verme.</span><span class="sxs-lookup"><span data-stu-id="dd858-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

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

## <a name="client"></a><span data-ttu-id="dd858-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="dd858-136">Client</span></span>

<span data-ttu-id="dd858-137">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="dd858-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="dd858-138">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="dd858-138">Do one of the following:</span></span>

- <span data-ttu-id="dd858-139">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd858-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="dd858-140">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd858-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="dd858-141">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd858-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="dd858-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dd858-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="dd858-143">Kod</span><span class="sxs-lookup"><span data-stu-id="dd858-143">Code</span></span>

<span data-ttu-id="dd858-144">Aşağıdaki kod, istemci bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd858-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="dd858-145">İleti modu güvenliği bağlama kullanır ve istemci kimlik bilgisi türü hiçbiri olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="dd858-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="dd858-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd858-146">Configuration</span></span>

<span data-ttu-id="dd858-147">Aşağıdaki kod, istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="dd858-147">The following code configures the client.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd858-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd858-148">See also</span></span>

- [<span data-ttu-id="dd858-149">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd858-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="dd858-150">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="dd858-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="dd858-151">İleti Güvenliği Anonim</span><span class="sxs-lookup"><span data-stu-id="dd858-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)
- [<span data-ttu-id="dd858-152">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="dd858-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="dd858-153">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="dd858-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
