---
description: 'Hakkında daha fazla bilgi edinin: <userPrincipalName>'
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 73ace3d6f3d5cb88f2630a4a2ae319decf420021
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664424"
---
# \<userPrincipalName>

<span data-ttu-id="7d89f-102">İstemci tarafından kimlik doğrulaması yapılacak bir hizmetin Kullanıcı asıl adını (UPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d89f-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="7d89f-103">UPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7d89f-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="7d89f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d89f-104">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d89f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d89f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7d89f-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="7d89f-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d89f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d89f-107">Attributes</span></span>  
  
|<span data-ttu-id="7d89f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d89f-108">Attribute</span></span>|<span data-ttu-id="7d89f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d89f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d89f-110">değer</span><span class="sxs-lookup"><span data-stu-id="7d89f-110">value</span></span>|<span data-ttu-id="7d89f-111">Kullanıcı hesabı adı (bazen Kullanıcı oturum açma adı olarak adlandırılır) ve Kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="7d89f-111">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="7d89f-112">Bu, bir Windows etki alanında oturum açmak için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="7d89f-112">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="7d89f-113">Biçim: someone@example.com (bir e-posta adresi için).</span><span class="sxs-lookup"><span data-stu-id="7d89f-113">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d89f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d89f-114">Child Elements</span></span>  

 <span data-ttu-id="7d89f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d89f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d89f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d89f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7d89f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d89f-117">Element</span></span>|<span data-ttu-id="7d89f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d89f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="7d89f-119">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d89f-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d89f-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d89f-120">Remarks</span></span>  

 <span data-ttu-id="7d89f-121">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken UPN 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d89f-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d89f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d89f-122">Example</span></span>  

 <span data-ttu-id="7d89f-123">Aşağıdaki yapılandırma kodu, istemci tarafından kimlik doğrulaması yapılacak hizmetin UPN 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d89f-123">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="7d89f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d89f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="7d89f-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="7d89f-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
