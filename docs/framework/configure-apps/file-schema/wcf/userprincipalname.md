---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 1bb0c8ac4cbe11cdfa31beb16b00b3863acabf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358683"
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="efe9f-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="efe9f-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="efe9f-103">Kullanıcı asıl adı (istemci tarafından doğrulanmasını UPN), bir hizmetin belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe9f-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="efe9f-104">UPN ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="efe9f-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="efe9f-105">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="efe9f-105">\<identity></span></span>  
<span data-ttu-id="efe9f-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="efe9f-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe9f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efe9f-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe9f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efe9f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="efe9f-109">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="efe9f-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe9f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efe9f-110">Attributes</span></span>  
  
|<span data-ttu-id="efe9f-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="efe9f-111">Attribute</span></span>|<span data-ttu-id="efe9f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efe9f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efe9f-113">value</span><span class="sxs-lookup"><span data-stu-id="efe9f-113">value</span></span>|<span data-ttu-id="efe9f-114">(Bazen kullanıcı oturum açma adı olarak adlandırılır) bir kullanıcı hesabı adı ve kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="efe9f-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="efe9f-115">Bu bir Windows etki alanında oturum açmak için standart kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="efe9f-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="efe9f-116">Biçim: someone@example.com (olduğu gibi bir e-posta adresi).</span><span class="sxs-lookup"><span data-stu-id="efe9f-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efe9f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efe9f-117">Child Elements</span></span>  
 <span data-ttu-id="efe9f-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="efe9f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efe9f-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efe9f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="efe9f-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="efe9f-120">Element</span></span>|<span data-ttu-id="efe9f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efe9f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe9f-122">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="efe9f-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="efe9f-123">İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe9f-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efe9f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efe9f-124">Remarks</span></span>  
 <span data-ttu-id="efe9f-125">Bu kimliğe sahip bir uç nokta bağlandığı güvenli bir Windows Communication Foundation (WCF) istemci SSPI kimlik doğrulama uç noktası ile gerçekleştirirken kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe9f-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efe9f-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="efe9f-126">Example</span></span>  
 <span data-ttu-id="efe9f-127">Aşağıdaki yapılandırma kodunu istemci tarafından doğrulanmasını UPN hizmetinin belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe9f-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="efe9f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efe9f-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="efe9f-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="efe9f-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="efe9f-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="efe9f-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
