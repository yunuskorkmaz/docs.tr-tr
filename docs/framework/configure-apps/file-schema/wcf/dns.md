---
title: '&lt;DNS&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2e3dbd0781485336a441c8eacb536ad008ff7a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdnsgt"></a><span data-ttu-id="bc76d-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="bc76d-102">&lt;dns&gt;</span></span>
<span data-ttu-id="bc76d-103">Sunucu beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc76d-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="bc76d-104">Bu kimlik X509 için geçerli olduğundan sunucu sertifikasının aynı değere sahip bir DNS içeriyorsa, sertifika kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="bc76d-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="bc76d-105">SPN aynı değere sahipse, aynı zamanda Windows kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc76d-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="bc76d-106">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bc76d-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="bc76d-107">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="bc76d-107">\<identity></span></span>  
<span data-ttu-id="bc76d-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="bc76d-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc76d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc76d-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc76d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc76d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc76d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc76d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc76d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc76d-112">Attributes</span></span>  
  
|<span data-ttu-id="bc76d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc76d-113">Attribute</span></span>|<span data-ttu-id="bc76d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc76d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc76d-115">value</span><span class="sxs-lookup"><span data-stu-id="bc76d-115">value</span></span>|<span data-ttu-id="bc76d-116">Sertifika DNS.</span><span class="sxs-lookup"><span data-stu-id="bc76d-116">The DNS of the certificate.</span></span> <span data-ttu-id="bc76d-117">DNS IP tabanlı bir ağda bilgisayarlar bulmak için kullanılan, endüstri standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="bc76d-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="bc76d-118">Kullanıcılar unutmayın görünen adları gibi [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) veya [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), 207.46.131.137 gibi sayı tabanlı adreslerini daha kolay.</span><span class="sxs-lookup"><span data-stu-id="bc76d-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc76d-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc76d-119">Child Elements</span></span>  
 <span data-ttu-id="bc76d-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc76d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc76d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc76d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bc76d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc76d-122">Element</span></span>|<span data-ttu-id="bc76d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc76d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc76d-124">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="bc76d-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="bc76d-125">İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc76d-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bc76d-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc76d-126">Example</span></span>  
 <span data-ttu-id="bc76d-127">Aşağıdaki yapılandırma kodunu bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası DNS belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc76d-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc76d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc76d-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="bc76d-129">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="bc76d-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="bc76d-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="bc76d-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
