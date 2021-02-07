---
description: 'Hakkında daha fazla bilgi edinin: <allowedAudienceUris>'
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: d556a9dcb71222ff52f38e43ad2608e1046e1a60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749980"
---
# \<allowedAudienceUris>

<span data-ttu-id="82f26-102"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="82f26-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="82f26-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="82f26-103">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82f26-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82f26-104">Attributes and Elements</span></span>  

 <span data-ttu-id="82f26-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="82f26-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82f26-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82f26-106">Attributes</span></span>  

 <span data-ttu-id="82f26-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="82f26-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="82f26-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82f26-108">Child Elements</span></span>  
  
|<span data-ttu-id="82f26-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="82f26-109">Element</span></span>|<span data-ttu-id="82f26-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82f26-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|<span data-ttu-id="82f26-111"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="82f26-111">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82f26-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82f26-112">Parent Elements</span></span>  
  
|<span data-ttu-id="82f26-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="82f26-113">Element</span></span>|<span data-ttu-id="82f26-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82f26-114">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="82f26-115">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f26-115">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82f26-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82f26-116">Remarks</span></span>  

 <span data-ttu-id="82f26-117">Bu koleksiyonu, güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir <xref:System.IdentityModel.Tokens.SamlSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="82f26-117">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="82f26-118">STS güvenlik belirtecini aldığında güvenlik belirtecinin bir güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> .</span><span class="sxs-lookup"><span data-stu-id="82f26-118">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="82f26-119">Bu, <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> alıcı Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="82f26-119">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="82f26-120">`audienceUriMode`Özniteliğini `<issuedTokenAuthentication>` veya olarak ayarlayın <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="82f26-120">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="82f26-121">URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="82f26-121">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="82f26-122">Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="82f26-122">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="82f26-123">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="82f26-123">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f26-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82f26-124">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="82f26-125">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="82f26-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="82f26-126">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="82f26-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="82f26-127">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82f26-127">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
