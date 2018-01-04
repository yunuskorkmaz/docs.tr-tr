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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c7585cfa85d805a3d1454b0c16e38eee297280a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdnsgt"></a><span data-ttu-id="c5e7a-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="c5e7a-102">&lt;dns&gt;</span></span>
<span data-ttu-id="c5e7a-103">Sunucu beklenen kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="c5e7a-104">Bu kimlik X509 için geçerli olduğundan sunucu sertifikasının aynı değere sahip bir DNS içeriyorsa, sertifika kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="c5e7a-105">SPN aynı değere sahipse, aynı zamanda Windows kimlik doğrulama modu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="c5e7a-106">Öğe değerini ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7a-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c5e7a-107">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c5e7a-107">\<identity></span></span>  
<span data-ttu-id="c5e7a-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="c5e7a-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e7a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5e7a-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5e7a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5e7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5e7a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5e7a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5e7a-112">Attributes</span></span>  
  
|<span data-ttu-id="c5e7a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5e7a-113">Attribute</span></span>|<span data-ttu-id="c5e7a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5e7a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5e7a-115">value</span><span class="sxs-lookup"><span data-stu-id="c5e7a-115">value</span></span>|<span data-ttu-id="c5e7a-116">Sertifika DNS.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-116">The DNS of the certificate.</span></span> <span data-ttu-id="c5e7a-117">DNS IP tabanlı bir ağda bilgisayarlar bulmak için kullanılan, endüstri standardı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="c5e7a-118">Kullanıcılar unutmayın görünen adları gibi [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) veya [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), 207.46.131.137 gibi sayı tabanlı adreslerini daha kolay.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5e7a-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5e7a-119">Child Elements</span></span>  
 <span data-ttu-id="c5e7a-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5e7a-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5e7a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c5e7a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5e7a-122">Element</span></span>|<span data-ttu-id="c5e7a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5e7a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5e7a-124">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c5e7a-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c5e7a-125">İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5e7a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5e7a-126">Example</span></span>  
 <span data-ttu-id="c5e7a-127">Aşağıdaki yapılandırma kodunu bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası DNS belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5e7a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5e7a-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="c5e7a-129">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c5e7a-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c5e7a-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c5e7a-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
