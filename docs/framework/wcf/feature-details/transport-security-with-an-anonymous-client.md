---
title: Anonim bir istemciyle aktarım güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: c3e44c87dfa70ac3a7acc5a83ac596efc22b6155
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344753"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="377e4-102">Anonim bir istemciyle aktarım güvenliği</span><span class="sxs-lookup"><span data-stu-id="377e4-102">Transport security with an anonymous client</span></span>

<span data-ttu-id="377e4-103">Bu Windows Communication Foundation (WCF) senaryosu gizlilik ve bütünlük sağlamak için taşıma güvenliği (HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="377e4-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="377e4-104">Sunucunun kimlik doğrulamasının Güvenli Yuva Katmanı (SSL) sertifikasıyla doğrulanması ve istemcilerin sunucunun sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="377e4-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="377e4-105">İstemcinin kimliği herhangi bir mekanizma tarafından doğrulanır ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="377e4-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="377e4-106">Örnek bir uygulama için bkz. [WS Transport Security](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="377e4-106">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="377e4-107">Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Aktarım güvenliğine genel bakış](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="377e4-107">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="377e4-108">Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve bir [SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="377e4-108">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Anonim bir istemciyle taşıma güvenliğini kullanma](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="377e4-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="377e4-110">Characteristic</span></span>|<span data-ttu-id="377e4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="377e4-111">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="377e4-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="377e4-112">Security Mode</span></span>|<span data-ttu-id="377e4-113">Aktarma</span><span class="sxs-lookup"><span data-stu-id="377e4-113">Transport</span></span>|
|<span data-ttu-id="377e4-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="377e4-114">Interoperability</span></span>|<span data-ttu-id="377e4-115">Mevcut Web Hizmetleri ve istemcilerle</span><span class="sxs-lookup"><span data-stu-id="377e4-115">With existing Web services and clients</span></span>|
|<span data-ttu-id="377e4-116">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="377e4-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="377e4-117">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="377e4-117">Authentication (Client)</span></span>|<span data-ttu-id="377e4-118">Evet</span><span class="sxs-lookup"><span data-stu-id="377e4-118">Yes</span></span><br /><br /> <span data-ttu-id="377e4-119">Uygulama düzeyi (WCF desteği yok)</span><span class="sxs-lookup"><span data-stu-id="377e4-119">Application level (no WCF support)</span></span>|
|<span data-ttu-id="377e4-120">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="377e4-120">Integrity</span></span>|<span data-ttu-id="377e4-121">Evet</span><span class="sxs-lookup"><span data-stu-id="377e4-121">Yes</span></span>|
|<span data-ttu-id="377e4-122">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="377e4-122">Confidentiality</span></span>|<span data-ttu-id="377e4-123">Evet</span><span class="sxs-lookup"><span data-stu-id="377e4-123">Yes</span></span>|
|<span data-ttu-id="377e4-124">Aktarma</span><span class="sxs-lookup"><span data-stu-id="377e4-124">Transport</span></span>|<span data-ttu-id="377e4-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="377e4-125">HTTPS</span></span>|
|<span data-ttu-id="377e4-126">Bağlama</span><span class="sxs-lookup"><span data-stu-id="377e4-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="377e4-127">Hizmet</span><span class="sxs-lookup"><span data-stu-id="377e4-127">Service</span></span>

<span data-ttu-id="377e4-128">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="377e4-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="377e4-129">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="377e4-129">Do one of the following:</span></span>

- <span data-ttu-id="377e4-130">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="377e4-130">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="377e4-131">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="377e4-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="377e4-132">Kod</span><span class="sxs-lookup"><span data-stu-id="377e4-132">Code</span></span>

<span data-ttu-id="377e4-133">Aşağıdaki kod, taşıma güvenliği kullanarak bir uç noktanın nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="377e4-133">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="377e4-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="377e4-134">Configuration</span></span>

<span data-ttu-id="377e4-135">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="377e4-135">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="377e4-136">İstemcinin kimliği herhangi bir mekanizma tarafından doğrulanır ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="377e4-136">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="377e4-137">İstemci</span><span class="sxs-lookup"><span data-stu-id="377e4-137">Client</span></span>

<span data-ttu-id="377e4-138">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="377e4-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="377e4-139">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="377e4-139">Do one of the following:</span></span>

- <span data-ttu-id="377e4-140">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="377e4-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="377e4-141">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="377e4-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="377e4-142">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="377e4-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="377e4-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="377e4-143">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="377e4-144">Kod</span><span class="sxs-lookup"><span data-stu-id="377e4-144">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="377e4-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="377e4-145">Configuration</span></span>

<span data-ttu-id="377e4-146">Hizmeti ayarlamak için aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="377e4-146">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="377e4-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="377e4-147">See also</span></span>

- [<span data-ttu-id="377e4-148">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="377e4-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="377e4-149">WS Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="377e4-149">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="377e4-150">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="377e4-150">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="377e4-151">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="377e4-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
