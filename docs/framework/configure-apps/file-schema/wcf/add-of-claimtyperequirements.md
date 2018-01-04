---
title: '&lt;claimTypeRequirements&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bc7fe3fec66b7fe09e8c6f8a6b437dcea2e3327
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="2cb10-102">&lt;claimTypeRequirements&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="2cb10-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="2cb10-103">Federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2cb10-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="2cb10-104">Örneğin, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik bilgilerini gereksinimleri Hizmetleri durumu.</span><span class="sxs-lookup"><span data-stu-id="2cb10-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="2cb10-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2cb10-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2cb10-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2cb10-106">\<bindings></span></span>  
<span data-ttu-id="2cb10-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2cb10-107">\<customBinding></span></span>  
<span data-ttu-id="2cb10-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2cb10-108">\<binding></span></span>  
<span data-ttu-id="2cb10-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="2cb10-109">\<security></span></span>  
<span data-ttu-id="2cb10-110">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="2cb10-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="2cb10-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2cb10-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb10-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cb10-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
           isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cb10-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cb10-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2cb10-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2cb10-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cb10-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2cb10-115">Attributes</span></span>  
  
|<span data-ttu-id="2cb10-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2cb10-116">Attribute</span></span>|<span data-ttu-id="2cb10-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cb10-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2cb10-118">claimType</span><span class="sxs-lookup"><span data-stu-id="2cb10-118">claimType</span></span>|<span data-ttu-id="2cb10-119">Bir talep türünü tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="2cb10-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="2cb10-120">Örneğin, bir Web sitesinden bir ürün satın almak için kullanıcının yeterli kredi limiti ile geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cb10-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="2cb10-121">Talep türü URI kredi kartı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2cb10-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="2cb10-122">isteğe bağlıdır</span><span class="sxs-lookup"><span data-stu-id="2cb10-122">isOptional</span></span>|<span data-ttu-id="2cb10-123">Bunun için isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="2cb10-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="2cb10-124">Bu öznitelik ayarlanırsa `false` bu gerekli bir talep ise.</span><span class="sxs-lookup"><span data-stu-id="2cb10-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="2cb10-125">Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cb10-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="2cb10-126">Örneğin, kullanıcının ilk adını girmesini gerektiriyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.</span><span class="sxs-lookup"><span data-stu-id="2cb10-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cb10-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cb10-127">Child Elements</span></span>  
 <span data-ttu-id="2cb10-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="2cb10-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cb10-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cb10-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2cb10-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="2cb10-130">Element</span></span>|<span data-ttu-id="2cb10-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cb10-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cb10-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2cb10-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="2cb10-133">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2cb10-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="2cb10-134">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="2cb10-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2cb10-135">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cb10-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2cb10-136">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2cb10-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cb10-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cb10-137">Remarks</span></span>  
 <span data-ttu-id="2cb10-138">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="2cb10-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2cb10-139">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cb10-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2cb10-140">Bu gereksinim, bir güvenlik ilkesi bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="2cb10-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="2cb10-141">Federasyon Hizmeti gereksinimlerini buna göre uygun kimlik bilgilerini vermek için istemci istekleri kimlik bilgileri, Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimlerini koyar.</span><span class="sxs-lookup"><span data-stu-id="2cb10-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb10-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cb10-142">Example</span></span>  
 <span data-ttu-id="2cb10-143">Aşağıdaki yapılandırma, güvenlik bağlamaya iki talep türü gereksinimlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="2cb10-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cb10-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cb10-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2cb10-145">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2cb10-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="2cb10-146">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2cb10-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2cb10-147">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2cb10-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2cb10-148">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2cb10-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2cb10-149">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2cb10-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="2cb10-150">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2cb10-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="2cb10-151">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="2cb10-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
