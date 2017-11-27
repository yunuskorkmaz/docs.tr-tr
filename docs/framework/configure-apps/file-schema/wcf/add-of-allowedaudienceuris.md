---
title: '&lt;allowedAudienceUris&gt; &lt;eklemesi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4de490107ed905b5acbda057f2cd53a306e6d75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a><span data-ttu-id="55bcf-102">&lt;allowedAudienceUris&gt; &lt;eklemesi&gt;</span><span class="sxs-lookup"><span data-stu-id="55bcf-102">&lt;add&gt; of &lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="55bcf-103">Hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="55bcf-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="55bcf-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="55bcf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="55bcf-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="55bcf-105">\<behaviors></span></span>  
<span data-ttu-id="55bcf-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="55bcf-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="55bcf-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="55bcf-107">\<behavior></span></span>  
<span data-ttu-id="55bcf-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="55bcf-108">\<serviceCredentials></span></span>  
<span data-ttu-id="55bcf-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="55bcf-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="55bcf-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="55bcf-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="55bcf-111">\<Ekle > öğesi için \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="55bcf-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55bcf-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55bcf-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55bcf-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55bcf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="55bcf-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55bcf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55bcf-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55bcf-115">Attributes</span></span>  
  
|<span data-ttu-id="55bcf-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55bcf-116">Attribute</span></span>|<span data-ttu-id="55bcf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55bcf-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55bcf-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="55bcf-118">allowedAudienceUri</span></span>|<span data-ttu-id="55bcf-119">Hedef URI içeren bir dize olan <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="55bcf-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55bcf-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55bcf-120">Child Elements</span></span>  
 <span data-ttu-id="55bcf-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="55bcf-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55bcf-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55bcf-122">Parent Elements</span></span>  
  
|<span data-ttu-id="55bcf-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="55bcf-123">Element</span></span>|<span data-ttu-id="55bcf-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55bcf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55bcf-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="55bcf-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="55bcf-126">Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="55bcf-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55bcf-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55bcf-127">Remarks</span></span>  
 <span data-ttu-id="55bcf-128">Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir federasyon uygulaması kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="55bcf-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="55bcf-129">Güvenlik belirteci STS gönderdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="55bcf-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="55bcf-130">İzin veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> verilen güvenlik belirteci bu Web hizmeti için bu onay aşağıdakileri yaparak olacağını belirterek hedeflenen doğrulamak alıcı Web hizmeti için:</span><span class="sxs-lookup"><span data-stu-id="55bcf-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="55bcf-131">Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="55bcf-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="55bcf-132">Bu koleksiyona URI'ler ekleyerek geçerli URI'ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="55bcf-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="55bcf-133">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="55bcf-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="55bcf-134">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="55bcf-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55bcf-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55bcf-135">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="55bcf-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="55bcf-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [<span data-ttu-id="55bcf-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="55bcf-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="55bcf-138">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="55bcf-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="55bcf-139">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="55bcf-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="55bcf-140">Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın</span><span class="sxs-lookup"><span data-stu-id="55bcf-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
