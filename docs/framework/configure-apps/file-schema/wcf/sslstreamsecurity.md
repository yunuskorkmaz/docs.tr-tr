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
ms.openlocfilehash: 5c801562339f02ff983bb5a755fda6718185ba5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="b341a-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="b341a-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="b341a-103">Bir SSL akışı kullanarak kanal güvenliği destekleyen bir özel bağlama öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b341a-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="b341a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b341a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b341a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b341a-105">\<bindings></span></span>  
<span data-ttu-id="b341a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b341a-106">\<customBinding></span></span>  
<span data-ttu-id="b341a-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b341a-107">\<binding></span></span>  
<span data-ttu-id="b341a-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="b341a-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b341a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b341a-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b341a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b341a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b341a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b341a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b341a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b341a-112">Attributes</span></span>  
  
|<span data-ttu-id="b341a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b341a-113">Attribute</span></span>|<span data-ttu-id="b341a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b341a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b341a-115">RequireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="b341a-115">requireClientCertificate</span></span>|<span data-ttu-id="b341a-116">Bir istemci sertifikası Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b341a-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="b341a-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b341a-117">The default is `false`.</span></span>|  
|<span data-ttu-id="b341a-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b341a-118">sslProtocols</span></span>|<span data-ttu-id="b341a-119">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b341a-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b341a-120">Varsayılan değer: Ssl3 &#124; TLS &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="b341a-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b341a-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b341a-121">Child Elements</span></span>  
 <span data-ttu-id="b341a-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="b341a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b341a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b341a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b341a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b341a-124">Element</span></span>|<span data-ttu-id="b341a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b341a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b341a-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b341a-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b341a-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b341a-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b341a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b341a-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="b341a-129">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b341a-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b341a-130">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="b341a-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b341a-131">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b341a-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b341a-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b341a-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
