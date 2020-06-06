---
title: <add> / <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153093"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="e6ad6-102">\<add> / \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e6ad6-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="e6ad6-103">Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="e6ad6-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e6ad6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6ad6-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6ad6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ad6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e6ad6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6ad6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6ad6-108">Attributes</span></span>  
  
|<span data-ttu-id="e6ad6-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6ad6-109">Attribute</span></span>|<span data-ttu-id="e6ad6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6ad6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6ad6-111">claimType</span><span class="sxs-lookup"><span data-stu-id="e6ad6-111">claimType</span></span>|<span data-ttu-id="e6ad6-112">Bir talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="e6ad6-113">Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="e6ad6-114">Talep türü kredi kartı URI 'SI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="e6ad6-115">IsOptional</span><span class="sxs-lookup"><span data-stu-id="e6ad6-115">isOptional</span></span>|<span data-ttu-id="e6ad6-116">Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="e6ad6-117">Bu gerekli bir talep ise, bu özniteliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="e6ad6-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="e6ad6-118">Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="e6ad6-119">Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6ad6-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ad6-120">Child Elements</span></span>  
 <span data-ttu-id="e6ad6-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6ad6-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ad6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e6ad6-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6ad6-123">Element</span></span>|<span data-ttu-id="e6ad6-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6ad6-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="e6ad6-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="e6ad6-126">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e6ad6-127">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e6ad6-128">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6ad6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6ad6-129">Remarks</span></span>  
 <span data-ttu-id="e6ad6-130">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e6ad6-131">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e6ad6-132">Bu gereksinim bir güvenlik ilkesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="e6ad6-133">İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ad6-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6ad6-134">Example</span></span>  
 <span data-ttu-id="e6ad6-135">Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="e6ad6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ad6-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="e6ad6-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e6ad6-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6ad6-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="e6ad6-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e6ad6-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e6ad6-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="e6ad6-140">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6ad6-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="e6ad6-141">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e6ad6-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
