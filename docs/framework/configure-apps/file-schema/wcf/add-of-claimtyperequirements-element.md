---
title: '&lt;claimTypeRequirements&gt; öğesi &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: fb5e723f6cff9f6e573a45a1dabe008beb9399e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687329"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="01d34-102">&lt;claimTypeRequirements&gt; öğesi &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="01d34-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="01d34-103">Birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="01d34-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="01d34-104">Örneğin, hizmetleri, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="01d34-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="01d34-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="01d34-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="01d34-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="01d34-106">\<bindings></span></span>  
<span data-ttu-id="01d34-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="01d34-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="01d34-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="01d34-108">\<binding></span></span>  
<span data-ttu-id="01d34-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="01d34-109">\<security></span></span>  
<span data-ttu-id="01d34-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="01d34-110">\<message></span></span>  
<span data-ttu-id="01d34-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="01d34-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d34-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01d34-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01d34-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="01d34-113">Attributes and Elements</span></span>  
 <span data-ttu-id="01d34-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01d34-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01d34-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01d34-115">Attributes</span></span>  
  
|<span data-ttu-id="01d34-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="01d34-116">Attribute</span></span>|<span data-ttu-id="01d34-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01d34-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01d34-118">ClaimType</span><span class="sxs-lookup"><span data-stu-id="01d34-118">claimType</span></span>|<span data-ttu-id="01d34-119">Bir talep türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="01d34-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="01d34-120">Örneğin, bir Web sitesine ait bir ürün satın almak için kullanıcının yeterli kredi sınırına geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d34-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="01d34-121">Talep türü URI kredi kartı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="01d34-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="01d34-122">isteğe bağlıdır</span><span class="sxs-lookup"><span data-stu-id="01d34-122">isOptional</span></span>|<span data-ttu-id="01d34-123">Bu isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="01d34-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="01d34-124">Bu öznitelik ayarlanan `false` bu gerekli bir talep ise.</span><span class="sxs-lookup"><span data-stu-id="01d34-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="01d34-125">Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d34-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="01d34-126">Örneğin, kullanıcının ilk adını girmesini gerekiyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.</span><span class="sxs-lookup"><span data-stu-id="01d34-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01d34-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="01d34-127">Child Elements</span></span>  
 <span data-ttu-id="01d34-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="01d34-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01d34-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="01d34-129">Parent Elements</span></span>  
  
|<span data-ttu-id="01d34-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="01d34-130">Element</span></span>|<span data-ttu-id="01d34-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01d34-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01d34-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="01d34-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="01d34-133">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="01d34-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="01d34-134">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="01d34-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="01d34-135">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="01d34-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="01d34-136">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d34-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="01d34-137">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="01d34-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d34-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01d34-138">Remarks</span></span>  
 <span data-ttu-id="01d34-139">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="01d34-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="01d34-140">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d34-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="01d34-141">Bu gereksinim, bir güvenlik ilkesinde bildirilen.</span><span class="sxs-lookup"><span data-stu-id="01d34-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="01d34-142">Buna göre gereksinimlerini karşılayan kimlik Federasyon Hizmeti verebilir böylece istemci istekleri kimlik bilgileri, bir Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimleri koyar.</span><span class="sxs-lookup"><span data-stu-id="01d34-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d34-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="01d34-143">Example</span></span>  
 <span data-ttu-id="01d34-144">Aşağıdaki yapılandırma, güvenlik bağlama iki talep türü gereksinimleri ekler.</span><span class="sxs-lookup"><span data-stu-id="01d34-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01d34-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01d34-145">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
