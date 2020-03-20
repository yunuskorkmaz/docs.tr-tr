---
title: <add> / <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153093"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="8452a-102">\<claimTypeRequirements \<>> ekleyin</span><span class="sxs-lookup"><span data-stu-id="8452a-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="8452a-103">Federe kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8452a-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="8452a-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgilerinin gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8452a-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="8452a-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8452a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8452a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8452a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="8452a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcı>**</span><span class="sxs-lookup"><span data-stu-id="8452a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8452a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlik>**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="8452a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParametreleri>**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="8452a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="8452a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="8452a-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="8452a-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8452a-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8452a-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8452a-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8452a-115">Attributes and Elements</span></span>  
 <span data-ttu-id="8452a-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8452a-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8452a-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8452a-117">Attributes</span></span>  
  
|<span data-ttu-id="8452a-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8452a-118">Attribute</span></span>|<span data-ttu-id="8452a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8452a-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8452a-120">Claimtype</span><span class="sxs-lookup"><span data-stu-id="8452a-120">claimType</span></span>|<span data-ttu-id="8452a-121">Bir talebin türünü tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="8452a-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="8452a-122">Örneğin, bir Web sitesinden ürün satın almak için, kullanıcının yeterli kredi limitine sahip geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8452a-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="8452a-123">Talep türü kredi kartı URI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8452a-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="8452a-124">ısoptional</span><span class="sxs-lookup"><span data-stu-id="8452a-124">isOptional</span></span>|<span data-ttu-id="8452a-125">Bu isteğe bağlı bir talep için olup olmadığını belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="8452a-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="8452a-126">Bu özniteliği, `false` gerekli bir talep olup olmadığını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8452a-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="8452a-127">Hizmet bazı bilgiler istediğinde ancak gerektirmediğinde bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8452a-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="8452a-128">Örneğin, kullanıcının ad, soyad ve adresini girmesini istiyorsanız, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="8452a-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8452a-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8452a-129">Child Elements</span></span>  
 <span data-ttu-id="8452a-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="8452a-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8452a-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8452a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="8452a-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="8452a-132">Element</span></span>|<span data-ttu-id="8452a-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8452a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8452a-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8452a-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="8452a-135">Gerekli talep türlerinin bir koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8452a-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="8452a-136">Federe bir senaryoda, hizmetler gelen kimlik bilgileri gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8452a-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8452a-137">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8452a-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8452a-138">Bu koleksiyondaki her öğe, federe bir kimlik bilgisi içinde görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8452a-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8452a-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8452a-139">Remarks</span></span>  
 <span data-ttu-id="8452a-140">Federe bir senaryoda, hizmetler gelen kimlik bilgileri gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8452a-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8452a-141">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8452a-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8452a-142">Bu gereksinim bir güvenlik ilkesinde kendini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8452a-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="8452a-143">İstemci federe bir hizmetten (örneğin, CardSpace) kimlik bilgileri istediğinde, gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar, böylece federe hizmet gereksinimleri karşılayan kimlik bilgilerini buna göre verebilir.</span><span class="sxs-lookup"><span data-stu-id="8452a-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8452a-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="8452a-144">Example</span></span>  
 <span data-ttu-id="8452a-145">Aşağıdaki yapılandırma, bir güvenlik bağlama iki talep türü gereksinimleri ekler.</span><span class="sxs-lookup"><span data-stu-id="8452a-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8452a-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8452a-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8452a-147">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8452a-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="8452a-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8452a-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8452a-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8452a-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8452a-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8452a-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8452a-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8452a-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="8452a-152">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8452a-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="8452a-153">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8452a-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
