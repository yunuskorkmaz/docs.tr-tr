---
title: Anonim bir istemciyle aktarım güvenliği
description: İstemcinin güvendiği bir sertifika kullanarak bir sunucunun kimliğini doğrulamak için aktarım güvenliği kullanan bu WCF senaryosunu inceleyin. İstemcinin kimliği doğrulanmadı.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245017"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="ba82f-104">Anonim bir istemciyle aktarım güvenliği</span><span class="sxs-lookup"><span data-stu-id="ba82f-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="ba82f-105">Bu Windows Communication Foundation (WCF) senaryosu gizlilik ve bütünlük sağlamak için taşıma güvenliği (HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba82f-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="ba82f-106">Sunucunun kimlik doğrulamasının Güvenli Yuva Katmanı (SSL) sertifikasıyla doğrulanması ve istemcilerin sunucunun sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba82f-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="ba82f-107">İstemcinin kimliği herhangi bir mekanizma tarafından doğrulanır ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="ba82f-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="ba82f-108">Örnek bir uygulama için bkz. [WS Transport Security](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="ba82f-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="ba82f-109">Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Aktarım güvenliğine genel bakış](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ba82f-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="ba82f-110">Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve bir [SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ba82f-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Anonim bir istemciyle taşıma güvenliğini kullanma](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="ba82f-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="ba82f-112">Characteristic</span></span>|<span data-ttu-id="ba82f-113">Description</span><span class="sxs-lookup"><span data-stu-id="ba82f-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="ba82f-114">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="ba82f-114">Security Mode</span></span>|<span data-ttu-id="ba82f-115">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ba82f-115">Transport</span></span>|
|<span data-ttu-id="ba82f-116">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="ba82f-116">Interoperability</span></span>|<span data-ttu-id="ba82f-117">Mevcut Web Hizmetleri ve istemcilerle</span><span class="sxs-lookup"><span data-stu-id="ba82f-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="ba82f-118">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="ba82f-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="ba82f-119">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="ba82f-119">Authentication (Client)</span></span>|<span data-ttu-id="ba82f-120">Yes</span><span class="sxs-lookup"><span data-stu-id="ba82f-120">Yes</span></span><br /><br /> <span data-ttu-id="ba82f-121">Uygulama düzeyi (WCF desteği yok)</span><span class="sxs-lookup"><span data-stu-id="ba82f-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="ba82f-122">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="ba82f-122">Integrity</span></span>|<span data-ttu-id="ba82f-123">Yes</span><span class="sxs-lookup"><span data-stu-id="ba82f-123">Yes</span></span>|
|<span data-ttu-id="ba82f-124">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="ba82f-124">Confidentiality</span></span>|<span data-ttu-id="ba82f-125">Yes</span><span class="sxs-lookup"><span data-stu-id="ba82f-125">Yes</span></span>|
|<span data-ttu-id="ba82f-126">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ba82f-126">Transport</span></span>|<span data-ttu-id="ba82f-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="ba82f-127">HTTPS</span></span>|
|<span data-ttu-id="ba82f-128">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ba82f-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="ba82f-129">Hizmet</span><span class="sxs-lookup"><span data-stu-id="ba82f-129">Service</span></span>

<span data-ttu-id="ba82f-130">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ba82f-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ba82f-131">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="ba82f-131">Do one of the following:</span></span>

- <span data-ttu-id="ba82f-132">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba82f-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="ba82f-133">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ba82f-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="ba82f-134">Kod</span><span class="sxs-lookup"><span data-stu-id="ba82f-134">Code</span></span>

<span data-ttu-id="ba82f-135">Aşağıdaki kod, taşıma güvenliği kullanarak bir uç noktanın nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ba82f-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="ba82f-136">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ba82f-136">Configuration</span></span>

<span data-ttu-id="ba82f-137">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ba82f-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="ba82f-138">İstemcinin kimliği herhangi bir mekanizma tarafından doğrulanır ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="ba82f-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="ba82f-139">İstemci</span><span class="sxs-lookup"><span data-stu-id="ba82f-139">Client</span></span>

<span data-ttu-id="ba82f-140">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ba82f-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ba82f-141">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="ba82f-141">Do one of the following:</span></span>

- <span data-ttu-id="ba82f-142">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="ba82f-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="ba82f-143">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba82f-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ba82f-144">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba82f-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ba82f-145">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ba82f-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="ba82f-146">Kod</span><span class="sxs-lookup"><span data-stu-id="ba82f-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="ba82f-147">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ba82f-147">Configuration</span></span>

<span data-ttu-id="ba82f-148">Hizmeti ayarlamak için aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba82f-148">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ba82f-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba82f-149">See also</span></span>

- [<span data-ttu-id="ba82f-150">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="ba82f-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="ba82f-151">WS Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ba82f-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="ba82f-152">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ba82f-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="ba82f-153">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ba82f-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
