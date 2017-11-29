---
title: '&lt;allowedAudienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b48449df95e9cf927cad805043c7419ec8c13be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="1b908-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="1b908-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="1b908-103">Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="1b908-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="1b908-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1b908-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b908-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="1b908-105">\<behaviors></span></span>  
<span data-ttu-id="1b908-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1b908-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1b908-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1b908-107">\<behavior></span></span>  
<span data-ttu-id="1b908-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1b908-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1b908-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1b908-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="1b908-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="1b908-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b908-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b908-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b908-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b908-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1b908-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="1b908-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b908-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b908-114">Attributes</span></span>  
 <span data-ttu-id="1b908-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b908-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b908-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b908-116">Child Elements</span></span>  
  
|<span data-ttu-id="1b908-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b908-117">Element</span></span>|<span data-ttu-id="1b908-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b908-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b908-119">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1b908-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="1b908-120">Hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="1b908-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b908-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b908-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1b908-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b908-122">Element</span></span>|<span data-ttu-id="1b908-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b908-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b908-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1b908-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="1b908-125">Bir hizmeti kimlik bilgileri verilen bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b908-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b908-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b908-126">Remarks</span></span>  
 <span data-ttu-id="1b908-127">Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir federasyon uygulaması kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="1b908-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="1b908-128">Güvenlik belirteci STS gönderdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="1b908-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="1b908-129">İzin veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> verilen güvenlik belirteci bu Web hizmeti için bu onay aşağıdakileri yaparak olacağını belirterek hedeflenen doğrulamak alıcı Web hizmeti için:</span><span class="sxs-lookup"><span data-stu-id="1b908-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="1b908-130">Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="1b908-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="1b908-131">Bu koleksiyona URI'ler ekleyerek geçerli URI'ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="1b908-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="1b908-132">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="1b908-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="1b908-133">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="1b908-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b908-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b908-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="1b908-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1b908-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="1b908-136">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1b908-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="1b908-137">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="1b908-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1b908-138">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="1b908-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1b908-139">Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın</span><span class="sxs-lookup"><span data-stu-id="1b908-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
