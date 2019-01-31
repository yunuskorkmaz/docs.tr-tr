---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a70c694509cd35e9bff7d56ae278da93b9b2b9ce
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273039"
---
# <a name="issuedtoken"></a><span data-ttu-id="0347f-101">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="0347f-101">\<issuedToken></span></span>
<span data-ttu-id="0347f-102">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0347f-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="0347f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0347f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0347f-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="0347f-104">\<behaviors></span></span>  
<span data-ttu-id="0347f-105">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="0347f-105">endpointBehaviors section</span></span>  
<span data-ttu-id="0347f-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="0347f-106">\<behavior></span></span>  
<span data-ttu-id="0347f-107">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0347f-107">\<clientCredentials></span></span>  
<span data-ttu-id="0347f-108">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="0347f-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0347f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0347f-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0347f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0347f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0347f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0347f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0347f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0347f-112">Attributes</span></span>  
  
|<span data-ttu-id="0347f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0347f-113">Attribute</span></span>|<span data-ttu-id="0347f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0347f-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="0347f-115">Belirteçleri önbelleğe yazılıp yazılmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0347f-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="0347f-116">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0347f-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="0347f-117">Hangi rastgele değerlerin (entropilerin) el sıkışma işlemlerinde kullanılacağını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0347f-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="0347f-118">Değerler `ClientEntropy`, `ServerEntropy`, ve `CombinedEntropy`, varsayılan `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="0347f-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="0347f-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="0347f-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="0347f-120">Geçerli saat (belirteç vericisi tarafından sağlanan) bir belirtecin yenilenmesinden önce geçebilecek çerçeve yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0347f-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="0347f-121">Değerler 0 ile 100 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="0347f-121">Values are from 0 to 100.</span></span> <span data-ttu-id="0347f-122">60 yenileme denenmeden önce %60 zaman geçiş belirten varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0347f-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="0347f-123">Verici ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0347f-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="0347f-124">Yerel verici ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0347f-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="0347f-125">Verilen belirteçler süreyi belirten isteğe bağlı Timespan özniteliği önbelleğe belirteç vericisinin (STS) bir süre belirtmediği.</span><span class="sxs-lookup"><span data-stu-id="0347f-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="0347f-126">Varsayılan değer "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="0347f-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0347f-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0347f-127">Child Elements</span></span>  
  
|<span data-ttu-id="0347f-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="0347f-128">Element</span></span>|<span data-ttu-id="0347f-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0347f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0347f-130">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="0347f-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="0347f-131">Belirteç uç noktası ile iletişim kurmak için kullanılan bağlama ve yerel dağıtımcının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0347f-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="0347f-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="0347f-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="0347f-133">Yerel verici ile iletişim kurarken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0347f-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0347f-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0347f-134">Parent Elements</span></span>  
  
|<span data-ttu-id="0347f-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="0347f-135">Element</span></span>|<span data-ttu-id="0347f-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0347f-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0347f-137">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0347f-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="0347f-138">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0347f-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0347f-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0347f-139">Remarks</span></span>  
 <span data-ttu-id="0347f-140">Verilen bir belirteç, örneğin, ile bir güvenli belirteç hizmeti (STS) bir Federasyon senaryosunda kimlik doğrulaması için kullanılan bir özel kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="0347f-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="0347f-141">Varsayılan olarak, SAML belirteci bir belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="0347f-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="0347f-142">Daha fazla bilgi için [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0347f-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="0347f-143">ve [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0347f-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="0347f-144">Bu bölümde, belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yerel yayımlayan yapılandırma için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0347f-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="0347f-145">Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="0347f-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0347f-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0347f-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="0347f-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="0347f-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0347f-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0347f-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0347f-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0347f-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0347f-150">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0347f-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="0347f-151">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="0347f-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0347f-152">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0347f-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="0347f-153">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0347f-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
