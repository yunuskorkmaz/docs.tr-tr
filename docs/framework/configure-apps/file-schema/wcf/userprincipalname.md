---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b93a0cc24953024e265df418ec6dd738598dd0f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="4960a-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="4960a-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="4960a-103">Kullanıcı asıl adı (istemci tarafından doğrulanmasını UPN), bir hizmetin belirtir.</span><span class="sxs-lookup"><span data-stu-id="4960a-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="4960a-104">UPN ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4960a-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="4960a-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4960a-105">\<identity></span></span>  
<span data-ttu-id="4960a-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="4960a-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4960a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4960a-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4960a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4960a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4960a-109">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="4960a-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4960a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4960a-110">Attributes</span></span>  
  
|<span data-ttu-id="4960a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4960a-111">Attribute</span></span>|<span data-ttu-id="4960a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4960a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4960a-113">value</span><span class="sxs-lookup"><span data-stu-id="4960a-113">value</span></span>|<span data-ttu-id="4960a-114">(Bazen kullanıcı oturum açma adı olarak adlandırılır) bir kullanıcı hesabı adı ve kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="4960a-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="4960a-115">Bu bir Windows etki alanında oturum açmak için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="4960a-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="4960a-116">Biçim: someone@example.com (olduğu gibi bir e-posta adresi).</span><span class="sxs-lookup"><span data-stu-id="4960a-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4960a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4960a-117">Child Elements</span></span>  
 <span data-ttu-id="4960a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="4960a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4960a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4960a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4960a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="4960a-120">Element</span></span>|<span data-ttu-id="4960a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4960a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4960a-122">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4960a-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4960a-123">İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4960a-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4960a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4960a-124">Remarks</span></span>  
 <span data-ttu-id="4960a-125">Güvenli [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Bu kimliğe sahip bir uç nokta bağlandığı istemcisi, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken UPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="4960a-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4960a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4960a-126">Example</span></span>  
 <span data-ttu-id="4960a-127">Aşağıdaki yapılandırma kodunu istemci tarafından doğrulanmasını UPN hizmetinin belirtir.</span><span class="sxs-lookup"><span data-stu-id="4960a-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4960a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4960a-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="4960a-129">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4960a-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="4960a-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4960a-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
