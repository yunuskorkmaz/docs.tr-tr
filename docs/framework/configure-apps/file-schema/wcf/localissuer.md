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
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="fa4e3-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="fa4e3-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="fa4e3-103">Bir güvenlik belirteci almak için kullanılacak yerel verenin bağlama ve adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="fa4e3-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa4e3-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-105">\<behaviors></span></span>  
<span data-ttu-id="fa4e3-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="fa4e3-106">endpointBehaviors section</span></span>  
<span data-ttu-id="fa4e3-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-107">\<behavior></span></span>  
<span data-ttu-id="fa4e3-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-108">\<clientCredentials></span></span>  
<span data-ttu-id="fa4e3-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-109">\<issuedToken></span></span>  
<span data-ttu-id="fa4e3-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4e3-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa4e3-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa4e3-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa4e3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fa4e3-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="fa4e3-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa4e3-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa4e3-114">Attributes</span></span>  
  
|<span data-ttu-id="fa4e3-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa4e3-115">Attribute</span></span>|<span data-ttu-id="fa4e3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa4e3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa4e3-117">adres</span><span class="sxs-lookup"><span data-stu-id="fa4e3-117">address</span></span>|<span data-ttu-id="fa4e3-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-118">Required string.</span></span> <span data-ttu-id="fa4e3-119">Yerel yayımlayan URI'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="fa4e3-120">bağlama</span><span class="sxs-lookup"><span data-stu-id="fa4e3-120">binding</span></span>|<span data-ttu-id="fa4e3-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-121">Optional string.</span></span> <span data-ttu-id="fa4e3-122">Sistem tarafından sağlanan bağlamalar biri.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-122">One of the system-provided bindings.</span></span> <span data-ttu-id="fa4e3-123">Bir listesi için bkz: [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="fa4e3-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="fa4e3-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa4e3-124">bindingConfiguration</span></span>|<span data-ttu-id="fa4e3-125">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-125">Optional string.</span></span> <span data-ttu-id="fa4e3-126">Yapılandırma dosyasında bulunan bir bağlama yapılandırması belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa4e3-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa4e3-127">Child Elements</span></span>  
  
|<span data-ttu-id="fa4e3-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa4e3-128">Element</span></span>|<span data-ttu-id="fa4e3-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa4e3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa4e3-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="fa4e3-131">Yerel yayımlayan için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="fa4e3-132">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="fa4e3-133">Doğru yerel yayımlayan değinmek için gerekli adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="fa4e3-134">Kullanabileceğiniz `add` üstbilgi bu koleksiyona eklemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa4e3-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa4e3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="fa4e3-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa4e3-136">Element</span></span>|<span data-ttu-id="fa4e3-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa4e3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa4e3-138">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="fa4e3-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="fa4e3-139">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa4e3-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa4e3-140">Remarks</span></span>  
 <span data-ttu-id="fa4e3-141">Bir güvenlik belirteci hizmeti (STS) verilen bir belirteç elde ederken istemci uygulaması yapılandırılmalıdır adres ve STS ile iletişim kurmak için kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="fa4e3-142">Zaman <xref:System.ServiceModel.WSFederationHttpBinding> bir URL veya güvenlik belirteci hizmeti için Federasyon bağlaması veren adresi http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous olduğunda sağlamaz veya `null`, istemcinin [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Kanal tarafından belirtilen değerleri kullanan `address` ve `binding` verilen belirteç edinme STS ile iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="fa4e3-143">Yerel yayımlayan yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="fa4e3-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa4e3-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa4e3-144">Example</span></span>  
 <span data-ttu-id="fa4e3-145">Aşağıdaki örnek kümeleri `address`, `binding`, ve `bindingConfiguration` özniteliklerini bir `localIssuer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa4e3-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa4e3-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="fa4e3-147">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="fa4e3-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="fa4e3-148">Nasıl yapılır: yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa4e3-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="fa4e3-149">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="fa4e3-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="fa4e3-150">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="fa4e3-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="fa4e3-151">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="fa4e3-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="fa4e3-152">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="fa4e3-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fa4e3-153">İstemcilerinin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="fa4e3-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="fa4e3-154">Nasıl yapılır: federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa4e3-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="fa4e3-155">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="fa4e3-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
