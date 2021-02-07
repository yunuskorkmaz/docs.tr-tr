---
description: 'Hakkında daha fazla bilgi edinin: <issuedToken>'
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: aa7486a621d5a6e6900f67300792e29ce2538257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725694"
---
# \<issuedToken>

<span data-ttu-id="c6a34-102">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="c6a34-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c6a34-103">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6a34-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6a34-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c6a34-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6a34-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6a34-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6a34-106">Attributes</span></span>  
  
|<span data-ttu-id="c6a34-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6a34-107">Attribute</span></span>|<span data-ttu-id="c6a34-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6a34-108">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="c6a34-109">Belirteçlerin önbelleğe alınıp alınmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6a34-109">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="c6a34-110">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c6a34-110">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="c6a34-111">El sıkışma işlemleri için hangi rastgele değerlerin (entropler) kullanıldığını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6a34-111">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="c6a34-112">Değerleri `ClientEntropy` ,, `ServerEntropy` ve değerleridir `CombinedEntropy` . varsayılan değer `CombinedEntropy` .</span><span class="sxs-lookup"><span data-stu-id="c6a34-112">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="c6a34-113">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .</span><span class="sxs-lookup"><span data-stu-id="c6a34-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="c6a34-114">Bir belirtecin yenilenmesinden önce geçebilen geçerli bir zaman çerçevesinin (belirteç veren tarafından sağlanan) yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6a34-114">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="c6a34-115">Değerler 0 ile 100 arasında değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-115">Values are from 0 to 100.</span></span> <span data-ttu-id="c6a34-116">Yenileme deneninceye kadar geçen sürenin %60 ' i belirten varsayılan değer 60 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-116">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="c6a34-117">Verenle iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c6a34-117">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="c6a34-118">Yerel veren ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c6a34-118">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="c6a34-119">Belirteç veren (STS) bir süre belirtmezse verilen belirteçlerin önbelleğe alındığı süreyi belirten isteğe bağlı TimeSpan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6a34-119">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="c6a34-120">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-120">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6a34-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6a34-121">Child Elements</span></span>  
  
|<span data-ttu-id="c6a34-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6a34-122">Element</span></span>|<span data-ttu-id="c6a34-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6a34-123">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="c6a34-124">Belirtecin yerel veren adresinin ve uç noktayla iletişim kurmak için kullanılan bağlamanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-124">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="c6a34-125">Yerel bir veren ile iletişim kurulurken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-125">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6a34-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6a34-126">Parent Elements</span></span>  
  
|<span data-ttu-id="c6a34-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6a34-127">Element</span></span>|<span data-ttu-id="c6a34-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6a34-128">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="c6a34-129">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6a34-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6a34-130">Remarks</span></span>  

 <span data-ttu-id="c6a34-131">Verilen belirteç, bir Federasyon senaryosunda güvenli bir belirteç hizmeti (STS) ile kimlik doğrulaması yapılırken kullanılan özel bir kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="c6a34-131">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="c6a34-132">Varsayılan olarak, belirteç bir SAML belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-132">By default, the token is a SAML token.</span></span> <span data-ttu-id="c6a34-133">Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md), [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="c6a34-133">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="c6a34-134">Bu bölüm, bir güvenlik belirteci hizmeti ile kullanılan bir belirteçleri yerel olarak veren veya davranışları yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c6a34-134">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="c6a34-135">Bir istemciyi yerel bir veren kullanacak şekilde yapılandırma yönergeleri için bkz. [nasıl yapılır: yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="c6a34-135">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a34-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6a34-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="c6a34-137">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c6a34-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c6a34-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c6a34-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c6a34-139">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c6a34-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c6a34-140">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c6a34-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c6a34-141">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6a34-141">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c6a34-142">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6a34-142">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="c6a34-143">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c6a34-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
