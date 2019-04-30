---
title: <add> ' ın <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 47eb9f95fd024b7df24a16781b3d89fe6deb0b8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701157"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="a2619-102">\<Ekle >, \<claimTypeRequirements > öğesi</span><span class="sxs-lookup"><span data-stu-id="a2619-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="a2619-103">Birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2619-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="a2619-104">Örneğin, hizmetleri, belirli bir talep türleri kümesini sahip olması gerekir gelen kimlik gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a2619-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="a2619-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a2619-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a2619-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a2619-106">\<bindings></span></span>  
<span data-ttu-id="a2619-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a2619-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a2619-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a2619-108">\<binding></span></span>  
<span data-ttu-id="a2619-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a2619-109">\<security></span></span>  
<span data-ttu-id="a2619-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a2619-110">\<message></span></span>  
<span data-ttu-id="a2619-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a2619-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2619-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2619-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2619-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2619-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a2619-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2619-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2619-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a2619-115">Attributes</span></span>  
  
|<span data-ttu-id="a2619-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a2619-116">Attribute</span></span>|<span data-ttu-id="a2619-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2619-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2619-118">ClaimType</span><span class="sxs-lookup"><span data-stu-id="a2619-118">claimType</span></span>|<span data-ttu-id="a2619-119">Bir talep türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="a2619-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="a2619-120">Örneğin, bir Web sitesine ait bir ürün satın almak için kullanıcının yeterli kredi sınırına geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2619-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="a2619-121">Talep türü URI kredi kartı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a2619-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="a2619-122">isteğe bağlıdır</span><span class="sxs-lookup"><span data-stu-id="a2619-122">isOptional</span></span>|<span data-ttu-id="a2619-123">Bu isteğe bağlı bir talep olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a2619-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="a2619-124">Bu öznitelik ayarlanan `false` bu gerekli bir talep ise.</span><span class="sxs-lookup"><span data-stu-id="a2619-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="a2619-125">Hizmet için bazı bilgiler ister, ancak gerekli olmadığı durumlarda bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2619-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="a2619-126">Örneğin, kullanıcının ilk adını girmesini gerekiyorsa, ad ve adres son ancak telefon numarası isteğe bağlı olduğuna karar.</span><span class="sxs-lookup"><span data-stu-id="a2619-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2619-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2619-127">Child Elements</span></span>  
 <span data-ttu-id="a2619-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2619-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2619-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2619-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a2619-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="a2619-130">Element</span></span>|<span data-ttu-id="a2619-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2619-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2619-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a2619-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="a2619-133">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2619-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a2619-134">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a2619-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a2619-135">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a2619-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a2619-136">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2619-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a2619-137">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2619-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2619-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2619-138">Remarks</span></span>  
 <span data-ttu-id="a2619-139">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a2619-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a2619-140">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2619-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a2619-141">Bu gereksinim, bir güvenlik ilkesinde bildirilen.</span><span class="sxs-lookup"><span data-stu-id="a2619-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="a2619-142">Buna göre gereksinimlerini karşılayan kimlik Federasyon Hizmeti verebilir böylece istemci istekleri kimlik bilgileri, bir Federasyon Hizmeti (örneğin, CardSpace) bir belirteç isteğini (RequestSecurityToken) gereksinimleri koyar.</span><span class="sxs-lookup"><span data-stu-id="a2619-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2619-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2619-143">Example</span></span>  
 <span data-ttu-id="a2619-144">Aşağıdaki yapılandırma, güvenlik bağlama iki talep türü gereksinimleri ekler.</span><span class="sxs-lookup"><span data-stu-id="a2619-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2619-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2619-145">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
