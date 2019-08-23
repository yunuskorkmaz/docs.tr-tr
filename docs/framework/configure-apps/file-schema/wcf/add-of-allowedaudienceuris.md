---
title: <add> / <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 64f0dd5c97ddfcd2fffd8ff4820d02af8c1ced54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926888"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="09e22-102">\<\<AllowedAudienceUris > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="09e22-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="09e22-103"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler.</span><span class="sxs-lookup"><span data-stu-id="09e22-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="09e22-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="09e22-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="09e22-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="09e22-105">\<behaviors></span></span>  
<span data-ttu-id="09e22-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="09e22-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="09e22-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="09e22-107">\<behavior></span></span>  
<span data-ttu-id="09e22-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="09e22-108">\<serviceCredentials></span></span>  
<span data-ttu-id="09e22-109">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="09e22-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="09e22-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="09e22-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="09e22-111">\<AllowedAudienceUris için \<> öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="09e22-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e22-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09e22-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09e22-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e22-113">Attributes and Elements</span></span>  
 <span data-ttu-id="09e22-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="09e22-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09e22-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="09e22-115">Attributes</span></span>  
  
|<span data-ttu-id="09e22-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="09e22-116">Attribute</span></span>|<span data-ttu-id="09e22-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e22-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09e22-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="09e22-118">allowedAudienceUri</span></span>|<span data-ttu-id="09e22-119"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="09e22-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09e22-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e22-120">Child Elements</span></span>  
 <span data-ttu-id="09e22-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="09e22-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09e22-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e22-122">Parent Elements</span></span>  
  
|<span data-ttu-id="09e22-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="09e22-123">Element</span></span>|<span data-ttu-id="09e22-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e22-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09e22-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="09e22-125">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="09e22-126"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09e22-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09e22-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09e22-127">Remarks</span></span>  
 <span data-ttu-id="09e22-128">Bu koleksiyonu, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="09e22-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="09e22-129">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="09e22-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="09e22-130">Bu, alıcı <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="09e22-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="09e22-131">`audienceUriMode` Özniteliğini veya olarak<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>ayarlayın. <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="09e22-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="09e22-132">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="09e22-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="09e22-133">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="09e22-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="09e22-134">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="09e22-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e22-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09e22-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="09e22-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="09e22-136">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="09e22-137">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="09e22-137">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="09e22-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="09e22-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="09e22-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="09e22-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="09e22-140">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="09e22-140">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
