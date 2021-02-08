---
description: 'Hakkında daha fazla bilgi <add> edinin: <allowedAudienceUris>'
title: <add> / <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: caa61da0ee7e00691213b95e31c943f5d81eea32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782214"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="2099a-103">\<add> / \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="2099a-103">\<add> of \<allowedAudienceUris></span></span>

<span data-ttu-id="2099a-104"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="2099a-104">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2099a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2099a-105">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2099a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2099a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2099a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2099a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2099a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2099a-108">Attributes</span></span>  
  
|<span data-ttu-id="2099a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2099a-109">Attribute</span></span>|<span data-ttu-id="2099a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2099a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2099a-111">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="2099a-111">allowedAudienceUri</span></span>|<span data-ttu-id="2099a-112"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI içeren dize <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="2099a-112">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2099a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2099a-113">Child Elements</span></span>  

 <span data-ttu-id="2099a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="2099a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2099a-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2099a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2099a-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="2099a-116">Element</span></span>|<span data-ttu-id="2099a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2099a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](allowedaudienceuris.md)|<span data-ttu-id="2099a-118"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="2099a-118">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2099a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2099a-119">Remarks</span></span>  

 <span data-ttu-id="2099a-120">Bu koleksiyonu, güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir <xref:System.IdentityModel.Tokens.SamlSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="2099a-120">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="2099a-121">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> .</span><span class="sxs-lookup"><span data-stu-id="2099a-121">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="2099a-122">Bu, <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> alıcı Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="2099a-122">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="2099a-123">`audienceUriMode`Özniteliğini `<issuedTokenAuthentication>` veya olarak ayarlayın <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="2099a-123">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="2099a-124">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="2099a-124">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="2099a-125">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="2099a-125">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="2099a-126">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="2099a-126">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2099a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2099a-127">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="2099a-128">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="2099a-128">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2099a-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2099a-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2099a-130">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2099a-130">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
