---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: b5ab3c3ad070499d686ea74b9fd459e89f380cfa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397970"
---
# <a name="issuedtoken"></a><span data-ttu-id="7e37c-101">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="7e37c-101">\<issuedToken></span></span>
<span data-ttu-id="7e37c-102">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="7e37c-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e37c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e37c-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7e37c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7e37c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7e37c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7e37c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7e37c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7e37c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7e37c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7e37c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="7e37c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="7e37c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuedToken >**</span><span class="sxs-lookup"><span data-stu-id="7e37c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e37c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e37c-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e37c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e37c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7e37c-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e37c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e37c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e37c-113">Attributes</span></span>  
  
|<span data-ttu-id="7e37c-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7e37c-114">Attribute</span></span>|<span data-ttu-id="7e37c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e37c-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="7e37c-116">Belirteçlerin önbelleğe alınıp alınmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e37c-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="7e37c-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="7e37c-118">El sıkışma işlemleri için hangi rastgele değerlerin (entropler) kullanıldığını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e37c-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="7e37c-119">`ClientEntropy`Değerleri, `ServerEntropy`, ve`CombinedEntropy`değerleridir .varsayılandeğer.`CombinedEntropy`</span><span class="sxs-lookup"><span data-stu-id="7e37c-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="7e37c-120">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="7e37c-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="7e37c-121">Bir belirtecin yenilenmesinden önce geçebilen geçerli bir zaman çerçevesinin (belirteç veren tarafından sağlanan) yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e37c-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="7e37c-122">Değerler 0 ile 100 arasında değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-122">Values are from 0 to 100.</span></span> <span data-ttu-id="7e37c-123">Yenileme deneninceye kadar geçen sürenin% 60 ' i belirten varsayılan değer 60 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="7e37c-124">Verenle iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7e37c-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="7e37c-125">Yerel veren ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7e37c-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="7e37c-126">Belirteç veren (STS) bir süre belirtmezse verilen belirteçlerin önbelleğe alındığı süreyi belirten isteğe bağlı TimeSpan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e37c-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="7e37c-127">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e37c-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e37c-128">Child Elements</span></span>  
  
|<span data-ttu-id="7e37c-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e37c-129">Element</span></span>|<span data-ttu-id="7e37c-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e37c-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e37c-131">\<LocalIssuer ></span><span class="sxs-lookup"><span data-stu-id="7e37c-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="7e37c-132">Belirtecin yerel veren adresinin ve uç noktayla iletişim kurmak için kullanılan bağlamanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="7e37c-133">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="7e37c-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="7e37c-134">Yerel bir veren ile iletişim kurulurken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e37c-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e37c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="7e37c-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e37c-136">Element</span></span>|<span data-ttu-id="7e37c-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e37c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e37c-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7e37c-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="7e37c-139">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e37c-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e37c-140">Remarks</span></span>  
 <span data-ttu-id="7e37c-141">Verilen belirteç, bir Federasyon senaryosunda güvenli bir belirteç hizmeti (STS) ile kimlik doğrulaması yapılırken kullanılan özel bir kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="7e37c-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="7e37c-142">Varsayılan olarak, belirteç bir SAML belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="7e37c-143">Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="7e37c-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="7e37c-144">ve [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="7e37c-144">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="7e37c-145">Bu bölüm, bir güvenlik belirteci hizmeti ile kullanılan bir belirteçleri yerel olarak veren veya davranışları yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7e37c-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="7e37c-146">Bir istemciyi yerel bir veren kullanmak üzere yapılandırmaya ilişkin yönergeler için bkz [. nasıl yapılır: Yerel bir veren](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7e37c-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e37c-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e37c-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="7e37c-148">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="7e37c-148">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7e37c-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7e37c-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7e37c-150">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="7e37c-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7e37c-151">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7e37c-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7e37c-152">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e37c-152">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="7e37c-153">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7e37c-153">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="7e37c-154">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="7e37c-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
