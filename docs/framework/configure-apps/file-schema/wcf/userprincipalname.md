---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 9e7b845d39495dba1d1a19af95faf308b8b8c0fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188257"
---
# <a name="userprincipalname"></a><span data-ttu-id="08123-101">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="08123-101">\<userPrincipalName></span></span>
<span data-ttu-id="08123-102">Kullanıcı asıl adı (istemci tarafından doğrulanacak UPN) bir hizmetin belirtir.</span><span class="sxs-lookup"><span data-stu-id="08123-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="08123-103">UPN ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="08123-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="08123-104">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="08123-104">\<identity></span></span>  
<span data-ttu-id="08123-105">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="08123-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08123-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08123-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08123-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="08123-107">Attributes and Elements</span></span>  
 <span data-ttu-id="08123-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08123-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08123-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08123-109">Attributes</span></span>  
  
|<span data-ttu-id="08123-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="08123-110">Attribute</span></span>|<span data-ttu-id="08123-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08123-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08123-112">value</span><span class="sxs-lookup"><span data-stu-id="08123-112">value</span></span>|<span data-ttu-id="08123-113">Bir kullanıcı hesabı adı (bazen kullanıcı oturum açma adı olarak adlandırılır) ve kullanıcı hesabının bulunduğu etki alanını tanıtan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="08123-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="08123-114">Bu, bir Windows etki alanında oturum açma için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="08123-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="08123-115">Biçim: someone@example.com (olduğu gibi bir e-posta adresi).</span><span class="sxs-lookup"><span data-stu-id="08123-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08123-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="08123-116">Child Elements</span></span>  
 <span data-ttu-id="08123-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="08123-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08123-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="08123-118">Parent Elements</span></span>  
  
|<span data-ttu-id="08123-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="08123-119">Element</span></span>|<span data-ttu-id="08123-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08123-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08123-121">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="08123-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="08123-122">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="08123-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08123-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08123-123">Remarks</span></span>  
 <span data-ttu-id="08123-124">Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken UPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="08123-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08123-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="08123-125">Example</span></span>  
 <span data-ttu-id="08123-126">İstemci tarafından doğrulanacak UPN hizmeti aşağıdaki yapılandırma kodunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="08123-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="08123-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08123-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="08123-128">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="08123-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="08123-129">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="08123-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
