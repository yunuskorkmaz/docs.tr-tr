---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c7e5c28325326d838da851ff4add12f8ae612c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="a35cc-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="a35cc-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="a35cc-103">Bir güvenlik belirteci almak için kullanılacak yerel verenin bağlama ve adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a35cc-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="a35cc-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a35cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a35cc-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="a35cc-105">\<behaviors></span></span>  
<span data-ttu-id="a35cc-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="a35cc-106">endpointBehaviors section</span></span>  
<span data-ttu-id="a35cc-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a35cc-107">\<behavior></span></span>  
<span data-ttu-id="a35cc-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a35cc-108">\<clientCredentials></span></span>  
<span data-ttu-id="a35cc-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="a35cc-109">\<issuedToken></span></span>  
<span data-ttu-id="a35cc-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="a35cc-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35cc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a35cc-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a35cc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a35cc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a35cc-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="a35cc-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a35cc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a35cc-114">Attributes</span></span>  
  
|<span data-ttu-id="a35cc-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a35cc-115">Attribute</span></span>|<span data-ttu-id="a35cc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a35cc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a35cc-117">adres</span><span class="sxs-lookup"><span data-stu-id="a35cc-117">address</span></span>|<span data-ttu-id="a35cc-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="a35cc-118">Required string.</span></span> <span data-ttu-id="a35cc-119">Yerel yayımlayan URI'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a35cc-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="a35cc-120">bağlama</span><span class="sxs-lookup"><span data-stu-id="a35cc-120">binding</span></span>|<span data-ttu-id="a35cc-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="a35cc-121">Optional string.</span></span> <span data-ttu-id="a35cc-122">Sistem tarafından sağlanan bağlamalar biri.</span><span class="sxs-lookup"><span data-stu-id="a35cc-122">One of the system-provided bindings.</span></span> <span data-ttu-id="a35cc-123">Bir listesi için bkz: [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a35cc-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="a35cc-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="a35cc-124">bindingConfiguration</span></span>|<span data-ttu-id="a35cc-125">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="a35cc-125">Optional string.</span></span> <span data-ttu-id="a35cc-126">Yapılandırma dosyasında bulunan bir bağlama yapılandırması belirtir.</span><span class="sxs-lookup"><span data-stu-id="a35cc-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a35cc-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a35cc-127">Child Elements</span></span>  
  
|<span data-ttu-id="a35cc-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="a35cc-128">Element</span></span>|<span data-ttu-id="a35cc-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a35cc-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a35cc-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="a35cc-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a35cc-131">Yerel yayımlayan için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a35cc-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="a35cc-132">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="a35cc-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="a35cc-133">Doğru yerel yayımlayan değinmek için gerekli adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a35cc-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="a35cc-134">Kullanabileceğiniz `add` üstbilgi bu koleksiyona eklemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a35cc-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a35cc-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a35cc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a35cc-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="a35cc-136">Element</span></span>|<span data-ttu-id="a35cc-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a35cc-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a35cc-138">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="a35cc-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="a35cc-139">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="a35cc-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a35cc-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a35cc-140">Remarks</span></span>  
 <span data-ttu-id="a35cc-141">Bir güvenlik belirteci hizmeti (STS) verilen bir belirteç elde ederken istemci uygulaması yapılandırılmalıdır adres ve STS ile iletişim kurmak için kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="a35cc-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="a35cc-142">Zaman <xref:System.ServiceModel.WSFederationHttpBinding> bir URL veya güvenlik belirteci hizmeti için Federasyon bağlaması veren adresi http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous olduğunda sağlamaz veya `null`, istemcinin [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Kanal tarafından belirtilen değerleri kullanan `address` ve `binding` verilen belirteç edinme STS ile iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="a35cc-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="a35cc-143">Yerel yayımlayan yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="a35cc-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a35cc-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="a35cc-144">Example</span></span>  
 <span data-ttu-id="a35cc-145">Aşağıdaki örnek kümeleri `address`, `binding`, ve `bindingConfiguration` özniteliklerini bir `localIssuer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a35cc-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a35cc-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a35cc-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="a35cc-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a35cc-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="a35cc-148">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a35cc-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="a35cc-149">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a35cc-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a35cc-150">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a35cc-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="a35cc-151">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a35cc-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a35cc-152">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a35cc-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a35cc-153">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a35cc-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="a35cc-154">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a35cc-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="a35cc-155">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a35cc-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
