---
title: <add> / <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: e15cb2d3e525d39a321bbe9760ddb8d72b02fffa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398352"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="8ae44-102">\<\<AllowedAudienceUris > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="8ae44-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="8ae44-103"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler.</span><span class="sxs-lookup"><span data-stu-id="8ae44-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="8ae44-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ae44-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8ae44-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8ae44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="8ae44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="8ae44-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="8ae44-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="8ae44-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowedAudienceUris >** ](allowedaudienceuris.md)</span><span class="sxs-lookup"><span data-stu-id="8ae44-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)</span></span>\
<span data-ttu-id="8ae44-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="8ae44-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae44-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ae44-113">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ae44-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ae44-114">Attributes and Elements</span></span>  
 <span data-ttu-id="8ae44-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ae44-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ae44-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ae44-116">Attributes</span></span>  
  
|<span data-ttu-id="8ae44-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ae44-117">Attribute</span></span>|<span data-ttu-id="8ae44-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ae44-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ae44-119">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="8ae44-119">allowedAudienceUri</span></span>|<span data-ttu-id="8ae44-120"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI içeren dize.</span><span class="sxs-lookup"><span data-stu-id="8ae44-120">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ae44-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ae44-121">Child Elements</span></span>  
 <span data-ttu-id="8ae44-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ae44-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ae44-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ae44-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8ae44-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ae44-124">Element</span></span>|<span data-ttu-id="8ae44-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ae44-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ae44-126">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="8ae44-126">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="8ae44-127"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ae44-127">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ae44-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ae44-128">Remarks</span></span>  
 <span data-ttu-id="8ae44-129">Bu koleksiyonu, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ae44-129">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="8ae44-130">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8ae44-130">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="8ae44-131">Bu, alıcı <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="8ae44-131">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="8ae44-132">`audienceUriMode` Özniteliğini veya olarak<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>ayarlayın. <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="8ae44-132">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="8ae44-133">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="8ae44-133">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="8ae44-134">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="8ae44-134">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="8ae44-135">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8ae44-135">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae44-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ae44-136">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="8ae44-137">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="8ae44-137">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="8ae44-138">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8ae44-138">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="8ae44-139">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="8ae44-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8ae44-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8ae44-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8ae44-141">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8ae44-141">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
