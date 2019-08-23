---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919971"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="eb730-101">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="eb730-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="eb730-102"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb730-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="eb730-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb730-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb730-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="eb730-104">\<behaviors></span></span>  
<span data-ttu-id="eb730-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="eb730-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="eb730-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="eb730-106">\<behavior></span></span>  
<span data-ttu-id="eb730-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="eb730-107">\<serviceCredentials></span></span>  
<span data-ttu-id="eb730-108">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="eb730-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="eb730-109">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="eb730-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb730-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb730-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb730-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb730-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eb730-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="eb730-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb730-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eb730-113">Attributes</span></span>  
 <span data-ttu-id="eb730-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="eb730-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb730-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb730-115">Child Elements</span></span>  
  
|<span data-ttu-id="eb730-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb730-116">Element</span></span>|<span data-ttu-id="eb730-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb730-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb730-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="eb730-118">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="eb730-119"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler.</span><span class="sxs-lookup"><span data-stu-id="eb730-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb730-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb730-120">Parent Elements</span></span>  
  
|<span data-ttu-id="eb730-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb730-121">Element</span></span>|<span data-ttu-id="eb730-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb730-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb730-123">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="eb730-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="eb730-124">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb730-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb730-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb730-125">Remarks</span></span>  
 <span data-ttu-id="eb730-126">Bu koleksiyonu, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb730-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="eb730-127">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="eb730-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="eb730-128">Bu, alıcı <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="eb730-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="eb730-129">`audienceUriMode` Özniteliğini veya olarak<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>ayarlayın. <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="eb730-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="eb730-130">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="eb730-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="eb730-131">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="eb730-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="eb730-132">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="eb730-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb730-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb730-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="eb730-134">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="eb730-134">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="eb730-135">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="eb730-135">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="eb730-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="eb730-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="eb730-137">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="eb730-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="eb730-138">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eb730-138">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
