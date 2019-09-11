---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854825"
---
# <a name="userprincipalname"></a><span data-ttu-id="9746c-101">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="9746c-101">\<userPrincipalName></span></span>
<span data-ttu-id="9746c-102">İstemci tarafından kimlik doğrulaması yapılacak bir hizmetin Kullanıcı asıl adını (UPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="9746c-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="9746c-103">UPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9746c-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="9746c-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9746c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9746c-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9746c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9746c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="9746c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="9746c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="9746c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="9746c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kimlik >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="9746c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="9746c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userPrincipalName >**</span><span class="sxs-lookup"><span data-stu-id="9746c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9746c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9746c-110">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9746c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9746c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9746c-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="9746c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9746c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9746c-113">Attributes</span></span>  
  
|<span data-ttu-id="9746c-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9746c-114">Attribute</span></span>|<span data-ttu-id="9746c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9746c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9746c-116">value</span><span class="sxs-lookup"><span data-stu-id="9746c-116">value</span></span>|<span data-ttu-id="9746c-117">Kullanıcı hesabı adı (bazen Kullanıcı oturum açma adı olarak adlandırılır) ve Kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="9746c-117">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="9746c-118">Bu, bir Windows etki alanında oturum açmak için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="9746c-118">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="9746c-119">Biçim: someone@example.com (bir e-posta adresi için).</span><span class="sxs-lookup"><span data-stu-id="9746c-119">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9746c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9746c-120">Child Elements</span></span>  
 <span data-ttu-id="9746c-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="9746c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9746c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9746c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9746c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9746c-123">Element</span></span>|<span data-ttu-id="9746c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9746c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9746c-125">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="9746c-125">\<identity></span></span>](identity.md)|<span data-ttu-id="9746c-126">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9746c-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9746c-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9746c-127">Remarks</span></span>  
 <span data-ttu-id="9746c-128">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken UPN 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9746c-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9746c-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="9746c-129">Example</span></span>  
 <span data-ttu-id="9746c-130">Aşağıdaki yapılandırma kodu, istemci tarafından kimlik doğrulaması yapılacak hizmetin UPN 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9746c-130">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="9746c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9746c-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="9746c-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="9746c-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9746c-133">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="9746c-133">\<identity></span></span>](identity.md)
