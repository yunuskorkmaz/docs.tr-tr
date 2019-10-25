---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846868"
---
# <a name="issuedtoken"></a><span data-ttu-id="4beb3-101">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="4beb3-101">\<issuedToken></span></span>
<span data-ttu-id="4beb3-102">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="4beb3-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4beb3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4beb3-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="4beb3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4beb3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışları >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4beb3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="4beb3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4beb3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="4beb3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4beb3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="4beb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="4beb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="4beb3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuedToken >**</span><span class="sxs-lookup"><span data-stu-id="4beb3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4beb3-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4beb3-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4beb3-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4beb3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4beb3-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4beb3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4beb3-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4beb3-113">Attributes</span></span>  
  
|<span data-ttu-id="4beb3-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4beb3-114">Attribute</span></span>|<span data-ttu-id="4beb3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4beb3-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="4beb3-116">Belirteçlerin önbelleğe alınıp alınmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4beb3-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="4beb3-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="4beb3-118">El sıkışma işlemleri için hangi rastgele değerlerin (entropler) kullanıldığını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4beb3-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="4beb3-119">Değerler `ClientEntropy`, `ServerEntropy`ve `CombinedEntropy`içerir, varsayılan `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="4beb3-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="4beb3-120">Bu öznitelik <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="4beb3-121">Bir belirtecin yenilenmesinden önce geçebilen geçerli bir zaman çerçevesinin (belirteç veren tarafından sağlanan) yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4beb3-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="4beb3-122">Değerler 0 ile 100 arasında değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-122">Values are from 0 to 100.</span></span> <span data-ttu-id="4beb3-123">Yenileme deneninceye kadar geçen sürenin %60 ' i belirten varsayılan değer 60 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="4beb3-124">Verenle iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4beb3-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="4beb3-125">Yerel veren ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4beb3-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="4beb3-126">Belirteç veren (STS) bir süre belirtmezse verilen belirteçlerin önbelleğe alındığı süreyi belirten isteğe bağlı TimeSpan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4beb3-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="4beb3-127">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4beb3-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4beb3-128">Child Elements</span></span>  
  
|<span data-ttu-id="4beb3-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="4beb3-129">Element</span></span>|<span data-ttu-id="4beb3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4beb3-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4beb3-131">\<LocalIssuer ></span><span class="sxs-lookup"><span data-stu-id="4beb3-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="4beb3-132">Belirtecin yerel veren adresinin ve uç noktayla iletişim kurmak için kullanılan bağlamanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="4beb3-133">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="4beb3-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="4beb3-134">Yerel bir veren ile iletişim kurulurken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4beb3-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4beb3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4beb3-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="4beb3-136">Element</span></span>|<span data-ttu-id="4beb3-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4beb3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4beb3-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="4beb3-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="4beb3-139">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4beb3-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4beb3-140">Remarks</span></span>  
 <span data-ttu-id="4beb3-141">Verilen belirteç, bir Federasyon senaryosunda güvenli bir belirteç hizmeti (STS) ile kimlik doğrulaması yapılırken kullanılan özel bir kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="4beb3-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="4beb3-142">Varsayılan olarak, belirteç bir SAML belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="4beb3-143">Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md), [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="4beb3-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="4beb3-144">Bu bölüm, bir güvenlik belirteci hizmeti ile kullanılan bir belirteçleri yerel olarak veren veya davranışları yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4beb3-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="4beb3-145">Bir istemciyi yerel bir veren kullanacak şekilde yapılandırma yönergeleri için bkz. [nasıl yapılır: yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="4beb3-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4beb3-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4beb3-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="4beb3-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="4beb3-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="4beb3-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4beb3-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4beb3-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4beb3-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4beb3-150">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4beb3-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="4beb3-151">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4beb3-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="4beb3-152">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4beb3-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="4beb3-153">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4beb3-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
