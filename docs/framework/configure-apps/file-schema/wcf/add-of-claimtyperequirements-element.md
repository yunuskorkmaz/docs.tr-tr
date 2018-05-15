---
title: '&lt;claimTypeRequirements&gt; öğesi &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 88e78db824d969c303fc5d494d4884c4d00284e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="a0d97-102">&lt;claimTypeRequirements&gt; öğesi &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="a0d97-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="a0d97-103">Federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0d97-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="a0d97-104">Örneğin, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik bilgilerini gereksinimleri Hizmetleri durumu.</span><span class="sxs-lookup"><span data-stu-id="a0d97-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="a0d97-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a0d97-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a0d97-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a0d97-106">\<bindings></span></span>  
<span data-ttu-id="a0d97-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a0d97-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a0d97-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a0d97-108">\<binding></span></span>  
<span data-ttu-id="a0d97-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a0d97-109">\<security></span></span>  
<span data-ttu-id="a0d97-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a0d97-110">\<message></span></span>  
<span data-ttu-id="a0d97-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a0d97-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d97-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0d97-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0d97-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d97-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a0d97-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0d97-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0d97-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0d97-115">Attributes</span></span>  
  
|<span data-ttu-id="a0d97-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0d97-116">Attribute</span></span>|<span data-ttu-id="a0d97-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d97-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0d97-118">claimType</span><span class="sxs-lookup"><span data-stu-id="a0d97-118">claimType</span></span>|<span data-ttu-id="a0d97-119">Bir talep türünü tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="a0d97-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="a0d97-120">Örneğin, bir Web sitesinden bir ürün satın almak için kullanıcının yeterli kredi limiti ile geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d97-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="a0d97-121">Talep türü URI kredi kartı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0d97-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="a0d97-122">isteğe bağlıdır</span><span class="sxs-lookup"><span data-stu-id="a0d97-122">isOptional</span></span>|<span data-ttu-id="a0d97-123">Bunun için isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a0d97-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="a0d97-124">Bu öznitelik ayarlanırsa `false` bu gerekli bir talep ise.</span><span class="sxs-lookup"><span data-stu-id="a0d97-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="a0d97-125">Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d97-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="a0d97-126">Örneğin, kullanıcının ilk adını girmesini gerektiriyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.</span><span class="sxs-lookup"><span data-stu-id="a0d97-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0d97-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d97-127">Child Elements</span></span>  
 <span data-ttu-id="a0d97-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0d97-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0d97-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d97-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a0d97-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0d97-130">Element</span></span>|<span data-ttu-id="a0d97-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d97-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0d97-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a0d97-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="a0d97-133">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0d97-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a0d97-134">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a0d97-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a0d97-135">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0d97-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a0d97-136">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d97-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a0d97-137">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0d97-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d97-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0d97-138">Remarks</span></span>  
 <span data-ttu-id="a0d97-139">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0d97-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a0d97-140">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d97-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a0d97-141">Bu gereksinim, bir güvenlik ilkesi bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="a0d97-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="a0d97-142">Federasyon Hizmeti gereksinimlerini buna göre uygun kimlik bilgilerini vermek için istemci istekleri kimlik bilgileri, Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimlerini koyar.</span><span class="sxs-lookup"><span data-stu-id="a0d97-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0d97-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0d97-143">Example</span></span>  
 <span data-ttu-id="a0d97-144">Aşağıdaki yapılandırma, güvenlik bağlamaya iki talep türü gereksinimlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="a0d97-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0d97-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0d97-145">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
