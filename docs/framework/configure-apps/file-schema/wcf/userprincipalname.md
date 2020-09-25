---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 353d3e2d88e3515e54deadab85c37ce3be26ef29
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203871"
---
# \<userPrincipalName>

<span data-ttu-id="b5edf-101">İstemci tarafından kimlik doğrulaması yapılacak bir hizmetin Kullanıcı asıl adını (UPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5edf-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="b5edf-102">UPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b5edf-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="b5edf-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5edf-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5edf-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5edf-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b5edf-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="b5edf-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5edf-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b5edf-106">Attributes</span></span>  
  
|<span data-ttu-id="b5edf-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b5edf-107">Attribute</span></span>|<span data-ttu-id="b5edf-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5edf-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5edf-109">değer</span><span class="sxs-lookup"><span data-stu-id="b5edf-109">value</span></span>|<span data-ttu-id="b5edf-110">Kullanıcı hesabı adı (bazen Kullanıcı oturum açma adı olarak adlandırılır) ve Kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="b5edf-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="b5edf-111">Bu, bir Windows etki alanında oturum açmak için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="b5edf-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="b5edf-112">Biçim: someone@example.com (bir e-posta adresi için).</span><span class="sxs-lookup"><span data-stu-id="b5edf-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5edf-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5edf-113">Child Elements</span></span>  

 <span data-ttu-id="b5edf-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5edf-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5edf-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5edf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b5edf-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b5edf-116">Element</span></span>|<span data-ttu-id="b5edf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5edf-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="b5edf-118">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5edf-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5edf-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5edf-119">Remarks</span></span>  

 <span data-ttu-id="b5edf-120">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken UPN 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5edf-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5edf-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5edf-121">Example</span></span>  

 <span data-ttu-id="b5edf-122">Aşağıdaki yapılandırma kodu, istemci tarafından kimlik doğrulaması yapılacak hizmetin UPN 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5edf-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="b5edf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5edf-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="b5edf-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b5edf-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
