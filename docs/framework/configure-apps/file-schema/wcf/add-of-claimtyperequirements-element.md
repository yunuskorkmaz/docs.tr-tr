---
title: <add><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 920d2b3fa4b51ee56e30863d521214ff66e7fcf2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149250"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="82083-102">\<add>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="82083-102">\<add> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="82083-103">Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82083-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="82083-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.</span><span class="sxs-lookup"><span data-stu-id="82083-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="82083-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="82083-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82083-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82083-106">Attributes and Elements</span></span>  

 <span data-ttu-id="82083-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82083-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82083-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82083-108">Attributes</span></span>  
  
|<span data-ttu-id="82083-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="82083-109">Attribute</span></span>|<span data-ttu-id="82083-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82083-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82083-111">claimType</span><span class="sxs-lookup"><span data-stu-id="82083-111">claimType</span></span>|<span data-ttu-id="82083-112">Bir talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="82083-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="82083-113">Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82083-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="82083-114">Talep türü kredi kartı URI 'SI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="82083-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="82083-115">IsOptional</span><span class="sxs-lookup"><span data-stu-id="82083-115">isOptional</span></span>|<span data-ttu-id="82083-116">Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="82083-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="82083-117">Bu gerekli bir talep ise, bu özniteliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="82083-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="82083-118">Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82083-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="82083-119">Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="82083-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82083-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82083-120">Child Elements</span></span>  

 <span data-ttu-id="82083-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="82083-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82083-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82083-122">Parent Elements</span></span>  
  
|<span data-ttu-id="82083-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="82083-123">Element</span></span>|<span data-ttu-id="82083-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82083-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="82083-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="82083-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="82083-126">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="82083-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="82083-127">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="82083-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="82083-128">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82083-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="82083-129">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82083-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82083-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82083-130">Remarks</span></span>  

 <span data-ttu-id="82083-131">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="82083-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="82083-132">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82083-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="82083-133">Bu gereksinim bir güvenlik ilkesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82083-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="82083-134">İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.</span><span class="sxs-lookup"><span data-stu-id="82083-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82083-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="82083-135">Example</span></span>  

 <span data-ttu-id="82083-136">Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.</span><span class="sxs-lookup"><span data-stu-id="82083-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82083-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82083-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
