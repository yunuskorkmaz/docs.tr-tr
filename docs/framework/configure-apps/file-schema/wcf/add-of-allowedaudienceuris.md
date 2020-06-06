---
title: <add> / <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: e15cb2d3e525d39a321bbe9760ddb8d72b02fffa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398352"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="06b22-102">\<add> / \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="06b22-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="06b22-103"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="06b22-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="06b22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06b22-104">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06b22-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="06b22-105">Attributes and Elements</span></span>  
 <span data-ttu-id="06b22-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06b22-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06b22-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06b22-107">Attributes</span></span>  
  
|<span data-ttu-id="06b22-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="06b22-108">Attribute</span></span>|<span data-ttu-id="06b22-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06b22-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06b22-110">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="06b22-110">allowedAudienceUri</span></span>|<span data-ttu-id="06b22-111"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI içeren dize <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="06b22-111">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06b22-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="06b22-112">Child Elements</span></span>  
 <span data-ttu-id="06b22-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="06b22-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06b22-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="06b22-114">Parent Elements</span></span>  
  
|<span data-ttu-id="06b22-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="06b22-115">Element</span></span>|<span data-ttu-id="06b22-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06b22-116">Description</span></span>|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](allowedaudienceuris.md)|<span data-ttu-id="06b22-117"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="06b22-117">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06b22-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06b22-118">Remarks</span></span>  
 <span data-ttu-id="06b22-119">Bu koleksiyonu, güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir <xref:System.IdentityModel.Tokens.SamlSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="06b22-119">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="06b22-120">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> .</span><span class="sxs-lookup"><span data-stu-id="06b22-120">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="06b22-121">Bu, <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> alıcı Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="06b22-121">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="06b22-122">`audienceUriMode`Özniteliğini `<issuedTokenAuthentication>` veya olarak ayarlayın <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="06b22-122">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="06b22-123">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="06b22-123">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="06b22-124">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="06b22-124">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="06b22-125">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="06b22-125">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b22-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06b22-126">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="06b22-127">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="06b22-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="06b22-128">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="06b22-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="06b22-129">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="06b22-129">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
