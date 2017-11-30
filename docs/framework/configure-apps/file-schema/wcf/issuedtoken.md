---
title: '&lt;IssuedToken&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9749386fbb2acd603cbfd0b74f37b65f0a59a6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="1b488-102">&lt;IssuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="1b488-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="1b488-103">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b488-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="1b488-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1b488-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b488-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="1b488-105">\<behaviors></span></span>  
<span data-ttu-id="1b488-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="1b488-106">endpointBehaviors section</span></span>  
<span data-ttu-id="1b488-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1b488-107">\<behavior></span></span>  
<span data-ttu-id="1b488-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1b488-108">\<clientCredentials></span></span>  
<span data-ttu-id="1b488-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="1b488-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b488-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b488-110">Syntax</span></span>  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b488-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b488-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1b488-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b488-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b488-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b488-113">Attributes</span></span>  
  
|<span data-ttu-id="1b488-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1b488-114">Attribute</span></span>|<span data-ttu-id="1b488-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b488-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="1b488-116">Belirteçleri önbelleğe alınıp alınmayacağını belirtir isteğe bağlı Boole öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1b488-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="1b488-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1b488-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="1b488-118">Hangi rastgele değerler (entropies) el sıkışması işlemleri için kullanılan belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1b488-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="1b488-119">Değerler `ClientEntropy`, `ServerEntropy`, ve `CombinedEntropy`, varsayılan `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="1b488-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="1b488-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="1b488-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="1b488-121">Geçerli saat (belirteci veren tarafından sağlanan) bir belirteç yenilenmeden önce bir geçirebilirsiniz çerçevesi yüzdesini belirtir isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1b488-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="1b488-122">Değerler 0 ile 100 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="1b488-122">Values are from 0 to 100.</span></span> <span data-ttu-id="1b488-123">60, yenileme denenmeden önce zaman geçişleri % 60 belirten varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1b488-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="1b488-124">Veren ile iletişim kurarken kullanması için kanal davranışları belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1b488-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="1b488-125">Yerel veren ile iletişim kurarken kullanması için kanal davranışları belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1b488-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="1b488-126">Verilen belirteçler süreyi belirten isteğe bağlı Timespan özniteliği önbelleğe alınır Belirteç Verenin (STS) birer belirtmediğinde.</span><span class="sxs-lookup"><span data-stu-id="1b488-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="1b488-127">Varsayılan değer "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="1b488-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b488-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b488-128">Child Elements</span></span>  
  
|<span data-ttu-id="1b488-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b488-129">Element</span></span>|<span data-ttu-id="1b488-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b488-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b488-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="1b488-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="1b488-132">Belirteç ve bağlama bitiş noktası ile iletişim kurmak için kullanılan yerel verenin adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b488-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="1b488-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1b488-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="1b488-134">Yerel yayımlayan kurulurken kullanmak için uç nokta davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b488-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b488-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b488-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1b488-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b488-136">Element</span></span>|<span data-ttu-id="1b488-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b488-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b488-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1b488-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="1b488-139">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b488-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b488-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b488-140">Remarks</span></span>  
 <span data-ttu-id="1b488-141">Verilen bir belirteç, örneğin, ile bir güvenli belirteç hizmeti (STS) Federasyon senaryosunda doğrulanırken kullanılan bir özel kimlik bilgileri türüdür.</span><span class="sxs-lookup"><span data-stu-id="1b488-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="1b488-142">Varsayılan olarak, bir SAML belirtecine bir belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="1b488-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="1b488-143">Daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="1b488-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="1b488-144">ve [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="1b488-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="1b488-145">Bu bölümde yerel yayımlayan belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1b488-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="1b488-146">Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="1b488-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b488-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b488-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="1b488-148">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="1b488-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1b488-149">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="1b488-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1b488-150">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="1b488-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1b488-151">İstemcilerinin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="1b488-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="1b488-152">Nasıl yapılır: federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b488-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="1b488-153">Nasıl yapılır: yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b488-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="1b488-154">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="1b488-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
