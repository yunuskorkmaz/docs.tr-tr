---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65233bf416080212a5c1447cffd329eca1b921f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="545d9-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="545d9-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="545d9-103">Bir SSL akışı kullanarak kanal güvenliği destekleyen bir özel bağlama öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="545d9-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="545d9-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="545d9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="545d9-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="545d9-105">\<bindings></span></span>  
<span data-ttu-id="545d9-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="545d9-106">\<customBinding></span></span>  
<span data-ttu-id="545d9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="545d9-107">\<binding></span></span>  
<span data-ttu-id="545d9-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="545d9-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545d9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="545d9-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="545d9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="545d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="545d9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="545d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="545d9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="545d9-112">Attributes</span></span>  
  
|<span data-ttu-id="545d9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="545d9-113">Attribute</span></span>|<span data-ttu-id="545d9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="545d9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="545d9-115">RequireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="545d9-115">requireClientCertificate</span></span>|<span data-ttu-id="545d9-116">Bir istemci sertifikası Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="545d9-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="545d9-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="545d9-117">The default is `false`.</span></span>|  
|<span data-ttu-id="545d9-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="545d9-118">sslProtocols</span></span>|<span data-ttu-id="545d9-119">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="545d9-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="545d9-120">Varsayılan değer: Ssl3 &#124; TLS &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="545d9-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="545d9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="545d9-121">Child Elements</span></span>  
 <span data-ttu-id="545d9-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="545d9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="545d9-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="545d9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="545d9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="545d9-124">Element</span></span>|<span data-ttu-id="545d9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="545d9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="545d9-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="545d9-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="545d9-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="545d9-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="545d9-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="545d9-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="545d9-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="545d9-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="545d9-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="545d9-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="545d9-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="545d9-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="545d9-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="545d9-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
