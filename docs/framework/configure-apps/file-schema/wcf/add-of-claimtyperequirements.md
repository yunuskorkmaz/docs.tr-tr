---
title: '&lt;claimTypeRequirements&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 5d4f0cd71ab9bf69921704300018207c9f7af107
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145217"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="cb179-102">&lt;claimTypeRequirements&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="cb179-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="cb179-103">Birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb179-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="cb179-104">Örneğin, hizmetleri, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="cb179-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="cb179-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cb179-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cb179-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cb179-106">\<bindings></span></span>  
<span data-ttu-id="cb179-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb179-107">\<customBinding></span></span>  
<span data-ttu-id="cb179-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb179-108">\<binding></span></span>  
<span data-ttu-id="cb179-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cb179-109">\<security></span></span>  
<span data-ttu-id="cb179-110">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="cb179-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="cb179-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cb179-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb179-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb179-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb179-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb179-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cb179-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb179-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb179-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb179-115">Attributes</span></span>  
  
|<span data-ttu-id="cb179-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb179-116">Attribute</span></span>|<span data-ttu-id="cb179-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb179-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb179-118">ClaimType</span><span class="sxs-lookup"><span data-stu-id="cb179-118">claimType</span></span>|<span data-ttu-id="cb179-119">Bir talep türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="cb179-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="cb179-120">Örneğin, bir Web sitesine ait bir ürün satın almak için kullanıcının yeterli kredi sınırına geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb179-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="cb179-121">Talep türü URI kredi kartı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="cb179-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="cb179-122">isteğe bağlıdır</span><span class="sxs-lookup"><span data-stu-id="cb179-122">isOptional</span></span>|<span data-ttu-id="cb179-123">Bu isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cb179-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="cb179-124">Bu öznitelik ayarlanan `false` bu gerekli bir talep ise.</span><span class="sxs-lookup"><span data-stu-id="cb179-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="cb179-125">Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb179-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="cb179-126">Örneğin, kullanıcının ilk adını girmesini gerekiyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.</span><span class="sxs-lookup"><span data-stu-id="cb179-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb179-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb179-127">Child Elements</span></span>  
 <span data-ttu-id="cb179-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb179-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb179-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb179-129">Parent Elements</span></span>  
  
|<span data-ttu-id="cb179-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb179-130">Element</span></span>|<span data-ttu-id="cb179-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb179-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb179-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cb179-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="cb179-133">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb179-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="cb179-134">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="cb179-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="cb179-135">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb179-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="cb179-136">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb179-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb179-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb179-137">Remarks</span></span>  
 <span data-ttu-id="cb179-138">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="cb179-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="cb179-139">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb179-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="cb179-140">Bu gereksinim, bir güvenlik ilkesinde bildirilen.</span><span class="sxs-lookup"><span data-stu-id="cb179-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="cb179-141">Buna göre gereksinimlerini karşılayan kimlik Federasyon Hizmeti verebilir böylece istemci istekleri kimlik bilgileri, bir Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimleri koyar.</span><span class="sxs-lookup"><span data-stu-id="cb179-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb179-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb179-142">Example</span></span>  
 <span data-ttu-id="cb179-143">Aşağıdaki yapılandırma, güvenlik bağlama iki talep türü gereksinimleri ekler.</span><span class="sxs-lookup"><span data-stu-id="cb179-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb179-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb179-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="cb179-145">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cb179-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="cb179-146">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb179-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cb179-147">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="cb179-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cb179-148">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb179-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cb179-149">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb179-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="cb179-150">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb179-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="cb179-151">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cb179-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
