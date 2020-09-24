---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9f3feb11fbe45cbb4b952c70feaa99f9c481dd2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157375"
---
# \<issuedToken>

<span data-ttu-id="c0056-101">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0056-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="c0056-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0056-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0056-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0056-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c0056-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0056-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0056-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0056-105">Attributes</span></span>  
  
|<span data-ttu-id="c0056-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c0056-106">Attribute</span></span>|<span data-ttu-id="c0056-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0056-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="c0056-108">Belirteçlerin önbelleğe alınıp alınmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c0056-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="c0056-109">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c0056-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="c0056-110">El sıkışma işlemleri için hangi rastgele değerlerin (entropler) kullanıldığını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c0056-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="c0056-111">Değerleri `ClientEntropy` ,, `ServerEntropy` ve değerleridir `CombinedEntropy` . varsayılan değer `CombinedEntropy` .</span><span class="sxs-lookup"><span data-stu-id="c0056-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="c0056-112">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .</span><span class="sxs-lookup"><span data-stu-id="c0056-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="c0056-113">Bir belirtecin yenilenmesinden önce geçebilen geçerli bir zaman çerçevesinin (belirteç veren tarafından sağlanan) yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c0056-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="c0056-114">Değerler 0 ile 100 arasında değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c0056-114">Values are from 0 to 100.</span></span> <span data-ttu-id="c0056-115">Yenileme deneninceye kadar geçen sürenin %60 ' i belirten varsayılan değer 60 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c0056-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="c0056-116">Verenle iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c0056-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="c0056-117">Yerel veren ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c0056-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="c0056-118">Belirteç veren (STS) bir süre belirtmezse verilen belirteçlerin önbelleğe alındığı süreyi belirten isteğe bağlı TimeSpan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c0056-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="c0056-119">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="c0056-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0056-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0056-120">Child Elements</span></span>  
  
|<span data-ttu-id="c0056-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0056-121">Element</span></span>|<span data-ttu-id="c0056-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0056-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="c0056-123">Belirtecin yerel veren adresinin ve uç noktayla iletişim kurmak için kullanılan bağlamanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0056-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="c0056-124">Yerel bir veren ile iletişim kurulurken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0056-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0056-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0056-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c0056-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0056-126">Element</span></span>|<span data-ttu-id="c0056-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0056-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="c0056-128">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0056-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0056-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0056-129">Remarks</span></span>  

 <span data-ttu-id="c0056-130">Verilen belirteç, bir Federasyon senaryosunda güvenli bir belirteç hizmeti (STS) ile kimlik doğrulaması yapılırken kullanılan özel bir kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="c0056-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="c0056-131">Varsayılan olarak, belirteç bir SAML belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="c0056-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="c0056-132">Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md), [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="c0056-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="c0056-133">Bu bölüm, bir güvenlik belirteci hizmeti ile kullanılan bir belirteçleri yerel olarak veren veya davranışları yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c0056-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="c0056-134">Bir istemciyi yerel bir veren kullanacak şekilde yapılandırma yönergeleri için bkz. [nasıl yapılır: yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="c0056-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0056-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0056-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="c0056-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c0056-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c0056-137">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c0056-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c0056-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c0056-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c0056-139">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c0056-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c0056-140">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0056-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c0056-141">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c0056-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="c0056-142">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c0056-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
