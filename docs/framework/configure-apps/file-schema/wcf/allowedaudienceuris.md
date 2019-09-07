---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398281"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="95d3b-101">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="95d3b-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="95d3b-102"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="95d3b-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="95d3b-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95d3b-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="95d3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="95d3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="95d3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="95d3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="95d3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="95d3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="95d3b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowedAudienceUris >**</span><span class="sxs-lookup"><span data-stu-id="95d3b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d3b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95d3b-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95d3b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95d3b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="95d3b-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="95d3b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95d3b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95d3b-114">Attributes</span></span>  
 <span data-ttu-id="95d3b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="95d3b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95d3b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95d3b-116">Child Elements</span></span>  
  
|<span data-ttu-id="95d3b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="95d3b-117">Element</span></span>|<span data-ttu-id="95d3b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95d3b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d3b-119">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="95d3b-119">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="95d3b-120"><xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler.</span><span class="sxs-lookup"><span data-stu-id="95d3b-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95d3b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95d3b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="95d3b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="95d3b-122">Element</span></span>|<span data-ttu-id="95d3b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95d3b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d3b-124">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="95d3b-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="95d3b-125">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="95d3b-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95d3b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95d3b-126">Remarks</span></span>  
 <span data-ttu-id="95d3b-127">Bu koleksiyonu, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95d3b-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="95d3b-128">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="95d3b-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="95d3b-129">Bu, alıcı <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="95d3b-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="95d3b-130">`audienceUriMode` Özniteliğini veya olarak<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>ayarlayın. <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="95d3b-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="95d3b-131">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="95d3b-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="95d3b-132">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="95d3b-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="95d3b-133">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="95d3b-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d3b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95d3b-134">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="95d3b-135">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="95d3b-135">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="95d3b-136">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="95d3b-136">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="95d3b-137">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="95d3b-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="95d3b-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="95d3b-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="95d3b-139">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="95d3b-139">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
