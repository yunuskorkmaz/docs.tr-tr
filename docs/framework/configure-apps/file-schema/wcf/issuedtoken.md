---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9a8d701e0806aae0a17a1c5ff7284606dd080f85
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750240"
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="5db91-102">&lt;IssuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="5db91-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="5db91-103">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="5db91-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="5db91-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5db91-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5db91-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5db91-105">\<behaviors></span></span>  
<span data-ttu-id="5db91-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="5db91-106">endpointBehaviors section</span></span>  
<span data-ttu-id="5db91-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5db91-107">\<behavior></span></span>  
<span data-ttu-id="5db91-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5db91-108">\<clientCredentials></span></span>  
<span data-ttu-id="5db91-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="5db91-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5db91-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5db91-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5db91-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5db91-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5db91-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5db91-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5db91-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5db91-113">Attributes</span></span>  
  
|<span data-ttu-id="5db91-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5db91-114">Attribute</span></span>|<span data-ttu-id="5db91-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5db91-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="5db91-116">Belirteçleri önbelleğe alınıp alınmayacağını belirtir isteğe bağlı Boole öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5db91-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="5db91-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5db91-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="5db91-118">Hangi rastgele değerler (entropies) el sıkışması işlemleri için kullanılan belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5db91-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="5db91-119">Değerler `ClientEntropy`, `ServerEntropy`, ve `CombinedEntropy`, varsayılan `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="5db91-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="5db91-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="5db91-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="5db91-121">Geçerli saat (belirteci veren tarafından sağlanan) bir belirteç yenilenmeden önce bir geçirebilirsiniz çerçevesi yüzdesini belirtir isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5db91-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="5db91-122">Değerler 0 ile 100 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="5db91-122">Values are from 0 to 100.</span></span> <span data-ttu-id="5db91-123">60, yenileme denenmeden önce zaman geçişleri % 60 belirten varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5db91-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="5db91-124">Veren ile iletişim kurarken kullanması için kanal davranışları belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5db91-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="5db91-125">Yerel veren ile iletişim kurarken kullanması için kanal davranışları belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5db91-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="5db91-126">Verilen belirteçler süreyi belirten isteğe bağlı Timespan özniteliği önbelleğe alınır Belirteç Verenin (STS) birer belirtmediğinde.</span><span class="sxs-lookup"><span data-stu-id="5db91-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="5db91-127">Varsayılan değer "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="5db91-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5db91-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5db91-128">Child Elements</span></span>  
  
|<span data-ttu-id="5db91-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="5db91-129">Element</span></span>|<span data-ttu-id="5db91-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5db91-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5db91-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="5db91-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="5db91-132">Belirteç ve bağlama bitiş noktası ile iletişim kurmak için kullanılan yerel verenin adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5db91-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="5db91-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5db91-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="5db91-134">Yerel yayımlayan kurulurken kullanmak için uç nokta davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="5db91-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5db91-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5db91-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5db91-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="5db91-136">Element</span></span>|<span data-ttu-id="5db91-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5db91-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5db91-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5db91-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5db91-139">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5db91-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5db91-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5db91-140">Remarks</span></span>  
 <span data-ttu-id="5db91-141">Verilen bir belirteç, örneğin, ile bir güvenli belirteç hizmeti (STS) Federasyon senaryosunda doğrulanırken kullanılan bir özel kimlik bilgileri türüdür.</span><span class="sxs-lookup"><span data-stu-id="5db91-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="5db91-142">Varsayılan olarak, bir SAML belirtecine bir belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="5db91-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="5db91-143">Daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5db91-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="5db91-144">ve [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5db91-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="5db91-145">Bu bölümde yerel yayımlayan belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5db91-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="5db91-146">Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="5db91-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db91-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5db91-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="5db91-148">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="5db91-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5db91-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5db91-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5db91-150">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="5db91-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="5db91-151">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5db91-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5db91-152">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5db91-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="5db91-153">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5db91-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="5db91-154">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="5db91-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
