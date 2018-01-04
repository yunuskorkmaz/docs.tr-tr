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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b10a0ef5718197464ffa40126f0a013d82256dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a><span data-ttu-id="f640b-102">&lt;allowedAudienceUris&gt; &lt;eklemesi&gt;</span><span class="sxs-lookup"><span data-stu-id="f640b-102">&lt;add&gt; of &lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="f640b-103">Hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="f640b-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="f640b-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f640b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f640b-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f640b-105">\<behaviors></span></span>  
<span data-ttu-id="f640b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f640b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f640b-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f640b-107">\<behavior></span></span>  
<span data-ttu-id="f640b-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f640b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f640b-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f640b-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="f640b-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="f640b-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="f640b-111">\<Ekle > öğesi için \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="f640b-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f640b-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f640b-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f640b-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f640b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f640b-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f640b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f640b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f640b-115">Attributes</span></span>  
  
|<span data-ttu-id="f640b-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f640b-116">Attribute</span></span>|<span data-ttu-id="f640b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f640b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f640b-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="f640b-118">allowedAudienceUri</span></span>|<span data-ttu-id="f640b-119">Hedef URI içeren bir dize olan <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="f640b-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f640b-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f640b-120">Child Elements</span></span>  
 <span data-ttu-id="f640b-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="f640b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f640b-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f640b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f640b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f640b-123">Element</span></span>|<span data-ttu-id="f640b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f640b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f640b-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="f640b-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="f640b-126">Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.</span><span class="sxs-lookup"><span data-stu-id="f640b-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f640b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f640b-127">Remarks</span></span>  
 <span data-ttu-id="f640b-128">Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir federasyon uygulaması kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="f640b-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="f640b-129">Güvenlik belirteci STS gönderdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="f640b-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="f640b-130">İzin veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> verilen güvenlik belirteci bu Web hizmeti için bu onay aşağıdakileri yaparak olacağını belirterek hedeflenen doğrulamak alıcı Web hizmeti için:</span><span class="sxs-lookup"><span data-stu-id="f640b-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="f640b-131">Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="f640b-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="f640b-132">Bu koleksiyona URI'ler ekleyerek geçerli URI'ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f640b-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="f640b-133">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="f640b-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="f640b-134">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="f640b-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f640b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f640b-135">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="f640b-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="f640b-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [<span data-ttu-id="f640b-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f640b-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="f640b-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="f640b-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="f640b-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f640b-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f640b-140">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f640b-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
