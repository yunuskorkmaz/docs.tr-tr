---
title: <add> , <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: a3ad50462cfa268a1826b62603110be3c5ba33db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148284"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="e9c2a-102">\<Ekle >, \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="e9c2a-103">Bir hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="e9c2a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e9c2a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9c2a-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-105">\<behaviors></span></span>  
<span data-ttu-id="e9c2a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e9c2a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e9c2a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-107">\<behavior></span></span>  
<span data-ttu-id="e9c2a-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e9c2a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="e9c2a-109">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="e9c2a-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="e9c2a-111">\<Ekle > öğesi için \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c2a-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9c2a-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9c2a-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9c2a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e9c2a-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9c2a-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9c2a-115">Attributes</span></span>  
  
|<span data-ttu-id="e9c2a-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e9c2a-116">Attribute</span></span>|<span data-ttu-id="e9c2a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9c2a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9c2a-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="e9c2a-118">allowedAudienceUri</span></span>|<span data-ttu-id="e9c2a-119">Bir hedef URI içeren bir dize olan <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9c2a-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9c2a-120">Child Elements</span></span>  
 <span data-ttu-id="e9c2a-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9c2a-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9c2a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e9c2a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9c2a-123">Element</span></span>|<span data-ttu-id="e9c2a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9c2a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9c2a-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="e9c2a-126">Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9c2a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9c2a-127">Remarks</span></span>  
 <span data-ttu-id="e9c2a-128">Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="e9c2a-129">Güvenlik belirteci STS verdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="e9c2a-130">Veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> alıcı Web hizmetinin aşağıdakileri yaparak bu denetimi olacağını belirleyerek verilen güvenlik belirteci için bu Web hizmetini kullandığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="e9c2a-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="e9c2a-131">Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="e9c2a-132">Bu koleksiyona bir URI'leri ekleyerek geçerli URI'lerin kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="e9c2a-133">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="e9c2a-134">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="e9c2a-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c2a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9c2a-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="e9c2a-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)
- [<span data-ttu-id="e9c2a-137">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e9c2a-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="e9c2a-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="e9c2a-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e9c2a-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e9c2a-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e9c2a-140">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9c2a-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
