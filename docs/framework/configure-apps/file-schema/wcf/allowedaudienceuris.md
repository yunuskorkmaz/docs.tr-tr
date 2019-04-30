---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: f758fc8e0934f56f9593246497d8aba5084c4a79
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673517"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="faf1c-101">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="faf1c-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="faf1c-102">Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="faf1c-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="faf1c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="faf1c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="faf1c-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="faf1c-104">\<behaviors></span></span>  
<span data-ttu-id="faf1c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="faf1c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="faf1c-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="faf1c-106">\<behavior></span></span>  
<span data-ttu-id="faf1c-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="faf1c-107">\<serviceCredentials></span></span>  
<span data-ttu-id="faf1c-108">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="faf1c-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="faf1c-109">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="faf1c-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf1c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="faf1c-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faf1c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="faf1c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="faf1c-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf1c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faf1c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="faf1c-113">Attributes</span></span>  
 <span data-ttu-id="faf1c-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="faf1c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="faf1c-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="faf1c-115">Child Elements</span></span>  
  
|<span data-ttu-id="faf1c-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="faf1c-116">Element</span></span>|<span data-ttu-id="faf1c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faf1c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faf1c-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="faf1c-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="faf1c-119">Bir hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="faf1c-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="faf1c-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="faf1c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="faf1c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="faf1c-121">Element</span></span>|<span data-ttu-id="faf1c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faf1c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faf1c-123">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="faf1c-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="faf1c-124">Bir hizmet kimlik bilgisi olarak verilen bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="faf1c-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faf1c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faf1c-125">Remarks</span></span>  
 <span data-ttu-id="faf1c-126">Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="faf1c-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="faf1c-127">Güvenlik belirteci STS verdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="faf1c-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="faf1c-128">Veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> alıcı Web hizmetinin aşağıdakileri yaparak bu denetimi olacağını belirleyerek verilen güvenlik belirteci için bu Web hizmetini kullandığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="faf1c-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="faf1c-129">Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="faf1c-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="faf1c-130">Bu koleksiyona bir URI'leri ekleyerek geçerli URI'lerin kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="faf1c-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="faf1c-131">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="faf1c-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="faf1c-132">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="faf1c-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf1c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faf1c-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="faf1c-134">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="faf1c-134">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="faf1c-135">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="faf1c-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)
- [<span data-ttu-id="faf1c-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="faf1c-136">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="faf1c-137">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="faf1c-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="faf1c-138">Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="faf1c-138">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
