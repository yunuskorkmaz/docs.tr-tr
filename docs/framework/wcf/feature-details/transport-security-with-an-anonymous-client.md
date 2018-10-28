---
title: Anonim İstemci ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 858ceb217ce30708a7d24c62ca18f8f59ba49d4c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183076"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="81a1d-102">Anonim İstemci ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="81a1d-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="81a1d-103">Windows Communication Foundation (WCF) Bu senaryo, gizliliği ve bütünlüğü sağlamak için Aktarım güvenliği (HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="81a1d-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="81a1d-104">Sunucu bir Güvenli Yuva Katmanı (SSL) sertifikası ile doğrulanması gerekir ve istemcilerin sunucu sertifikasına güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="81a1d-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="81a1d-105">İstemci tarafından herhangi bir mekanizma doğrulanmaz ve, bu nedenle, anonimdir.</span><span class="sxs-lookup"><span data-stu-id="81a1d-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="81a1d-106">Örnek bir uygulama için bkz: [WS aktarım güvenliği](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="81a1d-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> <span data-ttu-id="81a1d-107">Aktarım güvenliği hakkında daha fazla bilgi için bkz: [aktarım güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81a1d-107">For more information about transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 <span data-ttu-id="81a1d-108">Bir sertifika bir hizmetle kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="81a1d-108">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="81a1d-109">![Anonim istemci ile Aktarım güvenliği kullanarak](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="81a1d-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="81a1d-110">Özelliği</span><span class="sxs-lookup"><span data-stu-id="81a1d-110">Characteristic</span></span>|<span data-ttu-id="81a1d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81a1d-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="81a1d-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="81a1d-112">Security Mode</span></span>|<span data-ttu-id="81a1d-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="81a1d-113">Transport</span></span>|  
|<span data-ttu-id="81a1d-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="81a1d-114">Interoperability</span></span>|<span data-ttu-id="81a1d-115">Mevcut Web Hizmetleri ve istemcileri ile</span><span class="sxs-lookup"><span data-stu-id="81a1d-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="81a1d-116">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="81a1d-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="81a1d-117">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="81a1d-117">Authentication (Client)</span></span>|<span data-ttu-id="81a1d-118">Evet</span><span class="sxs-lookup"><span data-stu-id="81a1d-118">Yes</span></span><br /><br /> <span data-ttu-id="81a1d-119">Uygulama düzeyinde (WCF desteği)</span><span class="sxs-lookup"><span data-stu-id="81a1d-119">Application level (no WCF support)</span></span>|  
|<span data-ttu-id="81a1d-120">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="81a1d-120">Integrity</span></span>|<span data-ttu-id="81a1d-121">Evet</span><span class="sxs-lookup"><span data-stu-id="81a1d-121">Yes</span></span>|  
|<span data-ttu-id="81a1d-122">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="81a1d-122">Confidentiality</span></span>|<span data-ttu-id="81a1d-123">Evet</span><span class="sxs-lookup"><span data-stu-id="81a1d-123">Yes</span></span>|  
|<span data-ttu-id="81a1d-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="81a1d-124">Transport</span></span>|<span data-ttu-id="81a1d-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="81a1d-125">HTTPS</span></span>|  
|<span data-ttu-id="81a1d-126">Bağlama</span><span class="sxs-lookup"><span data-stu-id="81a1d-126">Binding</span></span>|<span data-ttu-id="81a1d-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="81a1d-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="81a1d-128">Hizmet</span><span class="sxs-lookup"><span data-stu-id="81a1d-128">Service</span></span>  
 <span data-ttu-id="81a1d-129">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="81a1d-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="81a1d-130">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="81a1d-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="81a1d-131">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="81a1d-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="81a1d-132">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="81a1d-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="81a1d-133">Kod</span><span class="sxs-lookup"><span data-stu-id="81a1d-133">Code</span></span>  
 <span data-ttu-id="81a1d-134">Aşağıdaki kod, aktarım güvenliği kullanarak bir uç nokta oluşturma işlemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="81a1d-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="81a1d-135">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81a1d-135">Configuration</span></span>  
 <span data-ttu-id="81a1d-136">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="81a1d-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="81a1d-137">İstemci, herhangi bir mekanizma tarafından doğrulanmaz ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="81a1d-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="81a1d-138">İstemci</span><span class="sxs-lookup"><span data-stu-id="81a1d-138">Client</span></span>  
 <span data-ttu-id="81a1d-139">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="81a1d-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="81a1d-140">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="81a1d-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="81a1d-141">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="81a1d-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="81a1d-142">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="81a1d-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="81a1d-143">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="81a1d-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="81a1d-144">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="81a1d-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="81a1d-145">Kod</span><span class="sxs-lookup"><span data-stu-id="81a1d-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="81a1d-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81a1d-146">Configuration</span></span>  
 <span data-ttu-id="81a1d-147">Aşağıdaki yapılandırmayı kod yerine barındırılan hizmeti kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81a1d-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81a1d-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81a1d-148">See Also</span></span>  
 [<span data-ttu-id="81a1d-149">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="81a1d-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="81a1d-150">WS Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="81a1d-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="81a1d-151">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="81a1d-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="81a1d-152">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="81a1d-152">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
