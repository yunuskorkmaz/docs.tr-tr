---
title: <add> / <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 7e7f0eac41e69e959aa6c4f8f3cfb488d4ea2917
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926793"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="cccb0-102">\<\<ClaimTypeRequirements > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="cccb0-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="cccb0-103">Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cccb0-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="cccb0-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.</span><span class="sxs-lookup"><span data-stu-id="cccb0-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="cccb0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cccb0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cccb0-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cccb0-106">\<bindings></span></span>  
<span data-ttu-id="cccb0-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cccb0-107">\<customBinding></span></span>  
<span data-ttu-id="cccb0-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cccb0-108">\<binding></span></span>  
<span data-ttu-id="cccb0-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cccb0-109">\<security></span></span>  
<span data-ttu-id="cccb0-110">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="cccb0-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="cccb0-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cccb0-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccb0-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cccb0-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cccb0-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cccb0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cccb0-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cccb0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cccb0-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cccb0-115">Attributes</span></span>  
  
|<span data-ttu-id="cccb0-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cccb0-116">Attribute</span></span>|<span data-ttu-id="cccb0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cccb0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cccb0-118">claimType</span><span class="sxs-lookup"><span data-stu-id="cccb0-118">claimType</span></span>|<span data-ttu-id="cccb0-119">Bir talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="cccb0-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="cccb0-120">Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cccb0-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="cccb0-121">Talep türü kredi kartı URI 'SI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="cccb0-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="cccb0-122">IsOptional</span><span class="sxs-lookup"><span data-stu-id="cccb0-122">isOptional</span></span>|<span data-ttu-id="cccb0-123">Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="cccb0-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="cccb0-124">Bu gerekli bir talep `false` ise, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cccb0-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="cccb0-125">Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cccb0-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="cccb0-126">Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="cccb0-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cccb0-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cccb0-127">Child Elements</span></span>  
 <span data-ttu-id="cccb0-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="cccb0-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cccb0-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cccb0-129">Parent Elements</span></span>  
  
|<span data-ttu-id="cccb0-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="cccb0-130">Element</span></span>|<span data-ttu-id="cccb0-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cccb0-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cccb0-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cccb0-132">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="cccb0-133">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cccb0-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="cccb0-134">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="cccb0-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="cccb0-135">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cccb0-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="cccb0-136">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cccb0-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cccb0-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cccb0-137">Remarks</span></span>  
 <span data-ttu-id="cccb0-138">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="cccb0-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="cccb0-139">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cccb0-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="cccb0-140">Bu gereksinim bir güvenlik ilkesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cccb0-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="cccb0-141">İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.</span><span class="sxs-lookup"><span data-stu-id="cccb0-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cccb0-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="cccb0-142">Example</span></span>  
 <span data-ttu-id="cccb0-143">Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.</span><span class="sxs-lookup"><span data-stu-id="cccb0-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cccb0-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cccb0-144">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cccb0-145">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cccb0-145">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="cccb0-146">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cccb0-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cccb0-147">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="cccb0-147">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cccb0-148">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cccb0-148">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cccb0-149">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cccb0-149">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="cccb0-150">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="cccb0-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="cccb0-151">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cccb0-151">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
