---
title: <add><claimTypeRequirements> öğesinin
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920203"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="d776c-102">\<\<ClaimTypeRequirements > öğesi > ekleyin</span><span class="sxs-lookup"><span data-stu-id="d776c-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="d776c-103">Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d776c-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="d776c-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.</span><span class="sxs-lookup"><span data-stu-id="d776c-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="d776c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d776c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d776c-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d776c-106">\<bindings></span></span>  
<span data-ttu-id="d776c-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="d776c-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d776c-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d776c-108">\<binding></span></span>  
<span data-ttu-id="d776c-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d776c-109">\<security></span></span>  
<span data-ttu-id="d776c-110">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="d776c-110">\<message></span></span>  
<span data-ttu-id="d776c-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d776c-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d776c-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d776c-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d776c-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d776c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d776c-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d776c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d776c-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d776c-115">Attributes</span></span>  
  
|<span data-ttu-id="d776c-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d776c-116">Attribute</span></span>|<span data-ttu-id="d776c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d776c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d776c-118">claimType</span><span class="sxs-lookup"><span data-stu-id="d776c-118">claimType</span></span>|<span data-ttu-id="d776c-119">Bir talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="d776c-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="d776c-120">Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d776c-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="d776c-121">Talep türü kredi kartı URI 'SI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d776c-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="d776c-122">IsOptional</span><span class="sxs-lookup"><span data-stu-id="d776c-122">isOptional</span></span>|<span data-ttu-id="d776c-123">Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="d776c-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="d776c-124">Bu gerekli bir talep `false` ise, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d776c-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="d776c-125">Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d776c-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="d776c-126">Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="d776c-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d776c-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d776c-127">Child Elements</span></span>  
 <span data-ttu-id="d776c-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="d776c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d776c-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d776c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d776c-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="d776c-130">Element</span></span>|<span data-ttu-id="d776c-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d776c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d776c-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d776c-132">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="d776c-133">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d776c-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d776c-134">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d776c-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d776c-135">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d776c-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d776c-136">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d776c-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d776c-137">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d776c-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d776c-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d776c-138">Remarks</span></span>  
 <span data-ttu-id="d776c-139">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d776c-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d776c-140">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d776c-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d776c-141">Bu gereksinim bir güvenlik ilkesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d776c-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="d776c-142">İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.</span><span class="sxs-lookup"><span data-stu-id="d776c-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d776c-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="d776c-143">Example</span></span>  
 <span data-ttu-id="d776c-144">Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.</span><span class="sxs-lookup"><span data-stu-id="d776c-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d776c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d776c-145">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
