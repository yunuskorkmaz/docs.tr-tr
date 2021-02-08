---
description: 'Hakkında daha fazla bilgi edinin: <add> <claimTypeRequirements> öğe'
title: <add><claimTypeRequirements>öğesinin
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 7ad93c4e1c2379704b38d3cdc68fddca62b3c057
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804042"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="6cea5-103">\<add>\<claimTypeRequirements>öğesinin</span><span class="sxs-lookup"><span data-stu-id="6cea5-103">\<add> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="6cea5-104">Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cea5-104">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="6cea5-105">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgileri için gereksinimleri durum.</span><span class="sxs-lookup"><span data-stu-id="6cea5-105">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="6cea5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6cea5-106">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cea5-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6cea5-107">Attributes and Elements</span></span>  

 <span data-ttu-id="6cea5-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6cea5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cea5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6cea5-109">Attributes</span></span>  
  
|<span data-ttu-id="6cea5-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6cea5-110">Attribute</span></span>|<span data-ttu-id="6cea5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cea5-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cea5-112">claimType</span><span class="sxs-lookup"><span data-stu-id="6cea5-112">claimType</span></span>|<span data-ttu-id="6cea5-113">Bir talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="6cea5-113">A URI that defines the type of a claim.</span></span> <span data-ttu-id="6cea5-114">Örneğin, bir ürünün bir Web sitesinden satın alınması için, kullanıcının yeterli kredi limiti olan geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cea5-114">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="6cea5-115">Talep türü kredi kartı URI 'SI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6cea5-115">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="6cea5-116">IsOptional</span><span class="sxs-lookup"><span data-stu-id="6cea5-116">isOptional</span></span>|<span data-ttu-id="6cea5-117">Bunun isteğe bağlı bir talep olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="6cea5-117">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="6cea5-118">Bu gerekli bir talep ise, bu özniteliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="6cea5-118">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="6cea5-119">Hizmet bazı bilgileri istediğinde ancak bunu gerektirmiyorsa bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cea5-119">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="6cea5-120">Örneğin, kullanıcının adını, soyadını ve adresini girmesini gerektiriyorsa, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="6cea5-120">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cea5-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6cea5-121">Child Elements</span></span>  

 <span data-ttu-id="6cea5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6cea5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cea5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6cea5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6cea5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6cea5-124">Element</span></span>|<span data-ttu-id="6cea5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cea5-125">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="6cea5-126">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cea5-126">Specifies a collection of required claim types.</span></span> <span data-ttu-id="6cea5-127">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="6cea5-127">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="6cea5-128">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6cea5-128">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6cea5-129">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cea5-129">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6cea5-130">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cea5-130">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cea5-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cea5-131">Remarks</span></span>  

 <span data-ttu-id="6cea5-132">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6cea5-132">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6cea5-133">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cea5-133">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6cea5-134">Bu gereksinim bir güvenlik ilkesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6cea5-134">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="6cea5-135">İstemci Federasyon hizmetinden kimlik bilgilerini istediğinde (örneğin, CardSpace), Federasyon hizmetinin gereksinimleri karşılayan kimlik bilgilerini vermesi için gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar.</span><span class="sxs-lookup"><span data-stu-id="6cea5-135">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cea5-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cea5-136">Example</span></span>  

 <span data-ttu-id="6cea5-137">Aşağıdaki yapılandırma, bir güvenlik bağlamaya iki talep türü gereksinimi ekler.</span><span class="sxs-lookup"><span data-stu-id="6cea5-137">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6cea5-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cea5-138">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
