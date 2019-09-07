---
title: <add> / <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 53da9dacbd3277bd8b608296a1515e3da7296f1c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398364"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="47653-102">\<\<ClaimTypeRequirements > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="47653-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="47653-103">Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47653-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="47653-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.</span><span class="sxs-lookup"><span data-stu-id="47653-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="47653-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="47653-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47653-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="47653-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="47653-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="47653-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="47653-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="47653-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="47653-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="47653-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="47653-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="47653-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="47653-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="47653-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="47653-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="47653-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="47653-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="47653-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47653-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47653-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47653-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47653-115">Attributes and Elements</span></span>  
 <span data-ttu-id="47653-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47653-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47653-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47653-117">Attributes</span></span>  
  
|<span data-ttu-id="47653-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47653-118">Attribute</span></span>|<span data-ttu-id="47653-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47653-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47653-120">claimType</span><span class="sxs-lookup"><span data-stu-id="47653-120">claimType</span></span>|<span data-ttu-id="47653-121">Bir talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="47653-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="47653-122">Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47653-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="47653-123">Talep türü kredi kartı URI 'SI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="47653-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="47653-124">IsOptional</span><span class="sxs-lookup"><span data-stu-id="47653-124">isOptional</span></span>|<span data-ttu-id="47653-125">Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="47653-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="47653-126">Bu gerekli bir talep `false` ise, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="47653-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="47653-127">Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47653-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="47653-128">Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="47653-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47653-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47653-129">Child Elements</span></span>  
 <span data-ttu-id="47653-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="47653-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47653-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47653-131">Parent Elements</span></span>  
  
|<span data-ttu-id="47653-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="47653-132">Element</span></span>|<span data-ttu-id="47653-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47653-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47653-134">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="47653-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="47653-135">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47653-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="47653-136">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="47653-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="47653-137">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47653-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="47653-138">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47653-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47653-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47653-139">Remarks</span></span>  
 <span data-ttu-id="47653-140">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="47653-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="47653-141">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47653-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="47653-142">Bu gereksinim bir güvenlik ilkesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="47653-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="47653-143">İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.</span><span class="sxs-lookup"><span data-stu-id="47653-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47653-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="47653-144">Example</span></span>  
 <span data-ttu-id="47653-145">Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.</span><span class="sxs-lookup"><span data-stu-id="47653-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47653-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47653-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="47653-147">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="47653-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="47653-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="47653-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="47653-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="47653-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="47653-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="47653-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="47653-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="47653-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="47653-152">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="47653-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="47653-153">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="47653-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
