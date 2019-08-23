---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940508"
---
# <a name="userprincipalname"></a><span data-ttu-id="045ca-101">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="045ca-101">\<userPrincipalName></span></span>
<span data-ttu-id="045ca-102">İstemci tarafından kimlik doğrulaması yapılacak bir hizmetin Kullanıcı asıl adını (UPN) belirtir.</span><span class="sxs-lookup"><span data-stu-id="045ca-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="045ca-103">UPN 'yi ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="045ca-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="045ca-104">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="045ca-104">\<identity></span></span>  
<span data-ttu-id="045ca-105">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="045ca-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045ca-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="045ca-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="045ca-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="045ca-107">Attributes and Elements</span></span>  
 <span data-ttu-id="045ca-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="045ca-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="045ca-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="045ca-109">Attributes</span></span>  
  
|<span data-ttu-id="045ca-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="045ca-110">Attribute</span></span>|<span data-ttu-id="045ca-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="045ca-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="045ca-112">value</span><span class="sxs-lookup"><span data-stu-id="045ca-112">value</span></span>|<span data-ttu-id="045ca-113">Kullanıcı hesabı adı (bazen Kullanıcı oturum açma adı olarak adlandırılır) ve Kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="045ca-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="045ca-114">Bu, bir Windows etki alanında oturum açmak için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="045ca-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="045ca-115">Biçim: someone@example.com (bir e-posta adresi için).</span><span class="sxs-lookup"><span data-stu-id="045ca-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="045ca-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="045ca-116">Child Elements</span></span>  
 <span data-ttu-id="045ca-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="045ca-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="045ca-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="045ca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="045ca-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="045ca-119">Element</span></span>|<span data-ttu-id="045ca-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="045ca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="045ca-121">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="045ca-121">\<identity></span></span>](identity.md)|<span data-ttu-id="045ca-122">İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="045ca-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="045ca-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="045ca-123">Remarks</span></span>  
 <span data-ttu-id="045ca-124">Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, uç noktayla SSPI kimlik doğrulaması gerçekleştirirken UPN 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="045ca-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="045ca-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="045ca-125">Example</span></span>  
 <span data-ttu-id="045ca-126">Aşağıdaki yapılandırma kodu, istemci tarafından kimlik doğrulaması yapılacak hizmetin UPN 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="045ca-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="045ca-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="045ca-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="045ca-128">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="045ca-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="045ca-129">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="045ca-129">\<identity></span></span>](identity.md)
