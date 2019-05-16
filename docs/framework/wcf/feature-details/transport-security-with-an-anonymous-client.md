---
title: Anonim istemci - WCF ile Aktarım güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: aac3b2ac6cfcca137bddaefafd290e744ee991eb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637435"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="e3fd2-102">Anonim istemci ile Aktarım güvenliği</span><span class="sxs-lookup"><span data-stu-id="e3fd2-102">Transport security with an anonymous client</span></span>

<span data-ttu-id="e3fd2-103">Windows Communication Foundation (WCF) Bu senaryo, gizliliği ve bütünlüğü sağlamak için Aktarım güvenliği (HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="e3fd2-104">Sunucu bir Güvenli Yuva Katmanı (SSL) sertifikası ile doğrulanması gerekir ve istemcilerin sunucu sertifikasına güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="e3fd2-105">İstemci tarafından herhangi bir mekanizma doğrulanmaz ve, bu nedenle, anonimdir.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="e3fd2-106">Örnek bir uygulama için bkz: [WS aktarım güvenliği](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="e3fd2-106">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="e3fd2-107">Aktarım güvenliği hakkında daha fazla bilgi için bkz: [aktarım güvenliğine genel bakış](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e3fd2-107">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="e3fd2-108">Bir sertifika bir hizmetle kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](working-with-certificates.md) ve [nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e3fd2-108">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Anonim istemci ile Aktarım güvenliği kullanarak](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="e3fd2-110">Özelliği</span><span class="sxs-lookup"><span data-stu-id="e3fd2-110">Characteristic</span></span>|<span data-ttu-id="e3fd2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3fd2-111">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="e3fd2-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="e3fd2-112">Security Mode</span></span>|<span data-ttu-id="e3fd2-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="e3fd2-113">Transport</span></span>|
|<span data-ttu-id="e3fd2-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e3fd2-114">Interoperability</span></span>|<span data-ttu-id="e3fd2-115">Mevcut Web Hizmetleri ve istemcileri ile</span><span class="sxs-lookup"><span data-stu-id="e3fd2-115">With existing Web services and clients</span></span>|
|<span data-ttu-id="e3fd2-116">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="e3fd2-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="e3fd2-117">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="e3fd2-117">Authentication (Client)</span></span>|<span data-ttu-id="e3fd2-118">Evet</span><span class="sxs-lookup"><span data-stu-id="e3fd2-118">Yes</span></span><br /><br /> <span data-ttu-id="e3fd2-119">Uygulama düzeyinde (WCF desteği)</span><span class="sxs-lookup"><span data-stu-id="e3fd2-119">Application level (no WCF support)</span></span>|
|<span data-ttu-id="e3fd2-120">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="e3fd2-120">Integrity</span></span>|<span data-ttu-id="e3fd2-121">Evet</span><span class="sxs-lookup"><span data-stu-id="e3fd2-121">Yes</span></span>|
|<span data-ttu-id="e3fd2-122">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="e3fd2-122">Confidentiality</span></span>|<span data-ttu-id="e3fd2-123">Evet</span><span class="sxs-lookup"><span data-stu-id="e3fd2-123">Yes</span></span>|
|<span data-ttu-id="e3fd2-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="e3fd2-124">Transport</span></span>|<span data-ttu-id="e3fd2-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="e3fd2-125">HTTPS</span></span>|
|<span data-ttu-id="e3fd2-126">Bağlama</span><span class="sxs-lookup"><span data-stu-id="e3fd2-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="e3fd2-127">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e3fd2-127">Service</span></span>

<span data-ttu-id="e3fd2-128">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e3fd2-129">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e3fd2-129">Do one of the following:</span></span>

- <span data-ttu-id="e3fd2-130">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-130">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="e3fd2-131">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="e3fd2-132">Kod</span><span class="sxs-lookup"><span data-stu-id="e3fd2-132">Code</span></span>

<span data-ttu-id="e3fd2-133">Aşağıdaki kod, aktarım güvenliği kullanarak bir uç nokta oluşturma işlemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e3fd2-133">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="e3fd2-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3fd2-134">Configuration</span></span>

<span data-ttu-id="e3fd2-135">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-135">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="e3fd2-136">İstemci, herhangi bir mekanizma tarafından doğrulanmaz ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-136">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="e3fd2-137">İstemci</span><span class="sxs-lookup"><span data-stu-id="e3fd2-137">Client</span></span>

<span data-ttu-id="e3fd2-138">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e3fd2-139">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e3fd2-139">Do one of the following:</span></span>

- <span data-ttu-id="e3fd2-140">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="e3fd2-141">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e3fd2-142">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e3fd2-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e3fd2-143">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="e3fd2-144">Kod</span><span class="sxs-lookup"><span data-stu-id="e3fd2-144">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="e3fd2-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3fd2-145">Configuration</span></span>

<span data-ttu-id="e3fd2-146">Aşağıdaki yapılandırmayı kod yerine barındırılan hizmeti kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-146">The following configuration can be used instead of the code to set up the service.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e3fd2-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3fd2-147">See also</span></span>

- [<span data-ttu-id="e3fd2-148">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3fd2-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="e3fd2-149">WS Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e3fd2-149">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="e3fd2-150">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3fd2-150">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="e3fd2-151">[Windows Server AppFabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e3fd2-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
