---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a06d59c5dfb14e5f3346ff2424339659568a369a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150194"
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="b2bf9-102">&lt;IssuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="b2bf9-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="b2bf9-103">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="b2bf9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2bf9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2bf9-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-105">\<behaviors></span></span>  
<span data-ttu-id="b2bf9-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="b2bf9-106">endpointBehaviors section</span></span>  
<span data-ttu-id="b2bf9-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-107">\<behavior></span></span>  
<span data-ttu-id="b2bf9-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-108">\<clientCredentials></span></span>  
<span data-ttu-id="b2bf9-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2bf9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2bf9-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2bf9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b2bf9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2bf9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-113">Attributes</span></span>  
  
|<span data-ttu-id="b2bf9-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b2bf9-114">Attribute</span></span>|<span data-ttu-id="b2bf9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bf9-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="b2bf9-116">Belirteçleri önbelleğe yazılıp yazılmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="b2bf9-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="b2bf9-118">Hangi rastgele değerlerin (entropilerin) el sıkışma işlemlerinde kullanılacağını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="b2bf9-119">Değerler `ClientEntropy`, `ServerEntropy`, ve `CombinedEntropy`, varsayılan `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="b2bf9-120">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="b2bf9-121">Geçerli saat (belirteç vericisi tarafından sağlanan) bir belirtecin yenilenmesinden önce geçebilecek çerçeve yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="b2bf9-122">Değerler 0 ile 100 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-122">Values are from 0 to 100.</span></span> <span data-ttu-id="b2bf9-123">60 yenileme denenmeden önce %60 zaman geçiş belirten varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="b2bf9-124">Verici ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="b2bf9-125">Yerel verici ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="b2bf9-126">Verilen belirteçler süreyi belirten isteğe bağlı Timespan özniteliği önbelleğe belirteç vericisinin (STS) bir süre belirtmediği.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="b2bf9-127">Varsayılan değer "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="b2bf9-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2bf9-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-128">Child Elements</span></span>  
  
|<span data-ttu-id="b2bf9-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2bf9-129">Element</span></span>|<span data-ttu-id="b2bf9-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bf9-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2bf9-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="b2bf9-132">Belirteç uç noktası ile iletişim kurmak için kullanılan bağlama ve yerel dağıtımcının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="b2bf9-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="b2bf9-134">Yerel verici ile iletişim kurarken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2bf9-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b2bf9-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2bf9-136">Element</span></span>|<span data-ttu-id="b2bf9-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bf9-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2bf9-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b2bf9-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="b2bf9-139">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2bf9-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2bf9-140">Remarks</span></span>  
 <span data-ttu-id="b2bf9-141">Verilen bir belirteç, örneğin, ile bir güvenli belirteç hizmeti (STS) bir Federasyon senaryosunda kimlik doğrulaması için kullanılan bir özel kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="b2bf9-142">Varsayılan olarak, SAML belirteci bir belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="b2bf9-143">Daha fazla bilgi için [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="b2bf9-144">ve [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="b2bf9-145">Bu bölümde, belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yerel yayımlayan yapılandırma için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="b2bf9-146">Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bf9-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="b2bf9-148">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="b2bf9-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b2bf9-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b2bf9-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b2bf9-150">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b2bf9-151">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b2bf9-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="b2bf9-152">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2bf9-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="b2bf9-153">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b2bf9-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="b2bf9-154">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
