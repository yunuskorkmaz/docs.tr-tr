---
title: <add>öğenin <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153106"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="fc866-102">\<claimTypeRequirements \<> öğesinin> ekleyin</span><span class="sxs-lookup"><span data-stu-id="fc866-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="fc866-103">Federe kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc866-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="fc866-104">Örneğin, hizmetler, belirli bir talep türü kümesine sahip olması gereken gelen kimlik bilgilerinin gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc866-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="fc866-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fc866-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fc866-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="fc866-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBağlayıcı>**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="fc866-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcı>**</span><span class="sxs-lookup"><span data-stu-id="fc866-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="fc866-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlik>**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="fc866-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<mesaj>**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="fc866-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="fc866-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="fc866-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="fc866-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="fc866-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc866-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc866-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc866-115">Attributes and Elements</span></span>  
 <span data-ttu-id="fc866-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc866-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc866-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc866-117">Attributes</span></span>  
  
|<span data-ttu-id="fc866-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc866-118">Attribute</span></span>|<span data-ttu-id="fc866-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc866-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc866-120">Claimtype</span><span class="sxs-lookup"><span data-stu-id="fc866-120">claimType</span></span>|<span data-ttu-id="fc866-121">Bir talebin türünü tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="fc866-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="fc866-122">Örneğin, bir Web sitesinden ürün satın almak için, kullanıcının yeterli kredi limitine sahip geçerli bir kredi kartı sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc866-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="fc866-123">Talep türü kredi kartı URI olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fc866-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="fc866-124">ısoptional</span><span class="sxs-lookup"><span data-stu-id="fc866-124">isOptional</span></span>|<span data-ttu-id="fc866-125">Bu isteğe bağlı bir talep için olup olmadığını belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="fc866-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="fc866-126">Bu özniteliği, `false` gerekli bir talep olup olmadığını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc866-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="fc866-127">Hizmet bazı bilgiler istediğinde ancak gerektirmediğinde bu özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc866-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="fc866-128">Örneğin, kullanıcının ad, soyad ve adresini girmesini istiyorsanız, ancak telefon numarasının isteğe bağlı olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="fc866-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc866-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc866-129">Child Elements</span></span>  
 <span data-ttu-id="fc866-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc866-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc866-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc866-131">Parent Elements</span></span>  
  
|<span data-ttu-id="fc866-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc866-132">Element</span></span>|<span data-ttu-id="fc866-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc866-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc866-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="fc866-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="fc866-135">Gerekli talep türlerinin bir koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc866-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="fc866-136">Her öğe türündedir. <xref:System.ServiceModel.Configuration.ClaimTypeElement></span><span class="sxs-lookup"><span data-stu-id="fc866-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="fc866-137">Federe bir senaryoda, hizmetler gelen kimlik bilgileri gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc866-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fc866-138">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc866-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fc866-139">Bu koleksiyondaki her öğe, federe bir kimlik bilgisi içinde görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc866-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc866-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc866-140">Remarks</span></span>  
 <span data-ttu-id="fc866-141">Federe bir senaryoda, hizmetler gelen kimlik bilgileri gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc866-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fc866-142">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc866-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fc866-143">Bu gereksinim bir güvenlik ilkesinde kendini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc866-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="fc866-144">İstemci federe bir hizmetten (örneğin, CardSpace) kimlik bilgileri istediğinde, gereksinimleri bir belirteç isteğine (RequestSecurityToken) koyar, böylece federe hizmet gereksinimleri karşılayan kimlik bilgilerini buna göre verebilir.</span><span class="sxs-lookup"><span data-stu-id="fc866-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc866-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc866-145">Example</span></span>  
 <span data-ttu-id="fc866-146">Aşağıdaki yapılandırma, bir güvenlik bağlama iki talep türü gereksinimleri ekler.</span><span class="sxs-lookup"><span data-stu-id="fc866-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc866-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc866-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
