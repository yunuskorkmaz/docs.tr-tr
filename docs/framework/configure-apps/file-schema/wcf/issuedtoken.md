---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925376"
---
# <a name="issuedtoken"></a><span data-ttu-id="a7e77-101">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="a7e77-101">\<issuedToken></span></span>
<span data-ttu-id="a7e77-102">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="a7e77-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7e77-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7e77-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a7e77-104">\<behaviors></span></span>  
<span data-ttu-id="a7e77-105">Endpointdavranışlar bölümü</span><span class="sxs-lookup"><span data-stu-id="a7e77-105">endpointBehaviors section</span></span>  
<span data-ttu-id="a7e77-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="a7e77-106">\<behavior></span></span>  
<span data-ttu-id="a7e77-107">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a7e77-107">\<clientCredentials></span></span>  
<span data-ttu-id="a7e77-108">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="a7e77-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e77-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e77-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7e77-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e77-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7e77-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7e77-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7e77-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7e77-112">Attributes</span></span>  
  
|<span data-ttu-id="a7e77-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7e77-113">Attribute</span></span>|<span data-ttu-id="a7e77-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e77-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="a7e77-115">Belirteçlerin önbelleğe alınıp alınmayacağını belirten isteğe bağlı Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a7e77-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="a7e77-116">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="a7e77-117">El sıkışma işlemleri için hangi rastgele değerlerin (entropler) kullanıldığını belirten isteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a7e77-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="a7e77-118">`ClientEntropy`Değerleri, `ServerEntropy`, ve`CombinedEntropy`değerleridir .varsayılandeğer.`CombinedEntropy`</span><span class="sxs-lookup"><span data-stu-id="a7e77-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="a7e77-119">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="a7e77-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="a7e77-120">Bir belirtecin yenilenmesinden önce geçebilen geçerli bir zaman çerçevesinin (belirteç veren tarafından sağlanan) yüzdesini belirten isteğe bağlı tamsayı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a7e77-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="a7e77-121">Değerler 0 ile 100 arasında değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-121">Values are from 0 to 100.</span></span> <span data-ttu-id="a7e77-122">Yenileme deneninceye kadar geçen sürenin% 60 ' i belirten varsayılan değer 60 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="a7e77-123">Verenle iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a7e77-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="a7e77-124">Yerel veren ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a7e77-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="a7e77-125">Belirteç veren (STS) bir süre belirtmezse verilen belirteçlerin önbelleğe alındığı süreyi belirten isteğe bağlı TimeSpan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a7e77-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="a7e77-126">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7e77-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e77-127">Child Elements</span></span>  
  
|<span data-ttu-id="a7e77-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7e77-128">Element</span></span>|<span data-ttu-id="a7e77-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e77-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7e77-130">\<LocalIssuer ></span><span class="sxs-lookup"><span data-stu-id="a7e77-130">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="a7e77-131">Belirtecin yerel veren adresinin ve uç noktayla iletişim kurmak için kullanılan bağlamanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="a7e77-132">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="a7e77-132">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="a7e77-133">Yerel bir veren ile iletişim kurulurken kullanılacak uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7e77-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e77-134">Parent Elements</span></span>  
  
|<span data-ttu-id="a7e77-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7e77-135">Element</span></span>|<span data-ttu-id="a7e77-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e77-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7e77-137">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a7e77-137">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="a7e77-138">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7e77-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7e77-139">Remarks</span></span>  
 <span data-ttu-id="a7e77-140">Verilen belirteç, bir Federasyon senaryosunda güvenli bir belirteç hizmeti (STS) ile kimlik doğrulaması yapılırken kullanılan özel bir kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="a7e77-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="a7e77-141">Varsayılan olarak, belirteç bir SAML belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="a7e77-142">Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="a7e77-142">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="a7e77-143">ve [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="a7e77-143">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="a7e77-144">Bu bölüm, bir güvenlik belirteci hizmeti ile kullanılan bir belirteçleri yerel olarak veren veya davranışları yapılandırmak için kullanılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a7e77-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="a7e77-145">Bir istemciyi yerel bir veren kullanmak üzere yapılandırmaya ilişkin yönergeler için bkz [. nasıl yapılır: Yerel bir veren](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a7e77-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e77-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e77-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="a7e77-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a7e77-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a7e77-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a7e77-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a7e77-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a7e77-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a7e77-150">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a7e77-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a7e77-151">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7e77-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a7e77-152">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a7e77-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a7e77-153">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a7e77-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
