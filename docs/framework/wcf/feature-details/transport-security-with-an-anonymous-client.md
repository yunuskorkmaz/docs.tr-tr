---
title: "Anonim İstemci ile Taşıma Güvenliği"
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
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 97a3c9c618fc7d6c96deba0b72e25ef36c5785e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="ed24e-102">Anonim İstemci ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ed24e-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="ed24e-103">Bu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] senaryosu, gizliliği ve bütünlük sağlamak için Aktarım güvenliği (HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed24e-103">This [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="ed24e-104">Sunucu ile Güvenli Yuva Katmanı (SSL) sertifikası kimlik doğrulaması gerekir ve istemcilerin sunucu sertifikasına güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed24e-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="ed24e-105">İstemci tarafından herhangi bir mekanizma doğrulanmaz ve, bu nedenle, anonim bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ed24e-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="ed24e-106">Örnek bir uygulama için bkz: [WS taşıma güvenliği](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="ed24e-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ed24e-107">Aktarım güvenliği için bkz: [taşıma güvenliği genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ed24e-107"> transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ed24e-108">bir sertifika bir hizmetle kullanma [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ed24e-108"> using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="ed24e-109">![Anonim istemci ile taşıma güvenliği kullanarak](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="ed24e-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="ed24e-110">Özelliği</span><span class="sxs-lookup"><span data-stu-id="ed24e-110">Characteristic</span></span>|<span data-ttu-id="ed24e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed24e-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ed24e-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="ed24e-112">Security Mode</span></span>|<span data-ttu-id="ed24e-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="ed24e-113">Transport</span></span>|  
|<span data-ttu-id="ed24e-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="ed24e-114">Interoperability</span></span>|<span data-ttu-id="ed24e-115">Mevcut Web Hizmetleri ve istemcileri ile</span><span class="sxs-lookup"><span data-stu-id="ed24e-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="ed24e-116">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="ed24e-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="ed24e-117">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="ed24e-117">Authentication (Client)</span></span>|<span data-ttu-id="ed24e-118">Evet</span><span class="sxs-lookup"><span data-stu-id="ed24e-118">Yes</span></span><br /><br /> <span data-ttu-id="ed24e-119">Uygulama düzeyinde (hiçbir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler)</span><span class="sxs-lookup"><span data-stu-id="ed24e-119">Application level (no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] support)</span></span>|  
|<span data-ttu-id="ed24e-120">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="ed24e-120">Integrity</span></span>|<span data-ttu-id="ed24e-121">Evet</span><span class="sxs-lookup"><span data-stu-id="ed24e-121">Yes</span></span>|  
|<span data-ttu-id="ed24e-122">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="ed24e-122">Confidentiality</span></span>|<span data-ttu-id="ed24e-123">Evet</span><span class="sxs-lookup"><span data-stu-id="ed24e-123">Yes</span></span>|  
|<span data-ttu-id="ed24e-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="ed24e-124">Transport</span></span>|<span data-ttu-id="ed24e-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="ed24e-125">HTTPS</span></span>|  
|<span data-ttu-id="ed24e-126">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ed24e-126">Binding</span></span>|<span data-ttu-id="ed24e-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="ed24e-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="ed24e-128">Hizmet</span><span class="sxs-lookup"><span data-stu-id="ed24e-128">Service</span></span>  
 <span data-ttu-id="ed24e-129">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ed24e-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ed24e-130">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="ed24e-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="ed24e-131">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed24e-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="ed24e-132">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ed24e-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed24e-133">Kod</span><span class="sxs-lookup"><span data-stu-id="ed24e-133">Code</span></span>  
 <span data-ttu-id="ed24e-134">Aşağıdaki kod taşıma güveliği kullanarak bir uç nokta oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ed24e-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="ed24e-135">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed24e-135">Configuration</span></span>  
 <span data-ttu-id="ed24e-136">Aşağıdaki kod Yapılandırması'nı kullanarak aynı uç nokta ayarlamayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed24e-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="ed24e-137">İstemci tarafından herhangi bir mekanizma doğrulanmaz ve bu nedenle anonimdir.</span><span class="sxs-lookup"><span data-stu-id="ed24e-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
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
  
## <a name="client"></a><span data-ttu-id="ed24e-138">İstemci</span><span class="sxs-lookup"><span data-stu-id="ed24e-138">Client</span></span>  
 <span data-ttu-id="ed24e-139">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ed24e-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ed24e-140">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="ed24e-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="ed24e-141">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed24e-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="ed24e-142">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed24e-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ed24e-143">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed24e-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ed24e-144">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ed24e-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="ed24e-145">Kod</span><span class="sxs-lookup"><span data-stu-id="ed24e-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="ed24e-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed24e-146">Configuration</span></span>  
 <span data-ttu-id="ed24e-147">Aşağıdaki yapılandırma hizmeti kurmak için kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed24e-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed24e-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed24e-148">See Also</span></span>  
 [<span data-ttu-id="ed24e-149">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed24e-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="ed24e-150">WS Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ed24e-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="ed24e-151">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed24e-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="ed24e-152">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="ed24e-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
