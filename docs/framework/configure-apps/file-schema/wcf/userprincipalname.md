---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: ff38a6975d1ec73c1a3014b94198ba630c3fec31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149986"
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="59b96-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="59b96-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="59b96-103">Kullanıcı asıl adı (istemci tarafından doğrulanacak UPN) bir hizmetin belirtir.</span><span class="sxs-lookup"><span data-stu-id="59b96-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="59b96-104">UPN ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="59b96-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="59b96-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="59b96-105">\<identity></span></span>  
<span data-ttu-id="59b96-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="59b96-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b96-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59b96-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59b96-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59b96-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59b96-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59b96-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59b96-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59b96-110">Attributes</span></span>  
  
|<span data-ttu-id="59b96-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59b96-111">Attribute</span></span>|<span data-ttu-id="59b96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59b96-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59b96-113">value</span><span class="sxs-lookup"><span data-stu-id="59b96-113">value</span></span>|<span data-ttu-id="59b96-114">Bir kullanıcı hesabı adı (bazen kullanıcı oturum açma adı olarak adlandırılır) ve kullanıcı hesabının bulunduğu etki alanını tanıtan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="59b96-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="59b96-115">Bu, bir Windows etki alanında oturum açma için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="59b96-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="59b96-116">Biçim: someone@example.com (olduğu gibi bir e-posta adresi).</span><span class="sxs-lookup"><span data-stu-id="59b96-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59b96-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59b96-117">Child Elements</span></span>  
 <span data-ttu-id="59b96-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="59b96-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59b96-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59b96-119">Parent Elements</span></span>  
  
|<span data-ttu-id="59b96-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="59b96-120">Element</span></span>|<span data-ttu-id="59b96-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59b96-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59b96-122">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="59b96-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="59b96-123">İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59b96-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59b96-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59b96-124">Remarks</span></span>  
 <span data-ttu-id="59b96-125">Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken UPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b96-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b96-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="59b96-126">Example</span></span>  
 <span data-ttu-id="59b96-127">İstemci tarafından doğrulanacak UPN hizmeti aşağıdaki yapılandırma kodunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="59b96-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="59b96-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59b96-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="59b96-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="59b96-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="59b96-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="59b96-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
