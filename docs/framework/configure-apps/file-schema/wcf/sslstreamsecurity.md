---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
ms.openlocfilehash: 6eacf1833ecf980696d75c5dbcaaba3ba6403d92
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196336"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="42f70-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="42f70-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="42f70-103">SSL akışı kullanarak kanal güvenliğini destekleyen özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42f70-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="42f70-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="42f70-104">\<system.serviceModel></span></span>  
<span data-ttu-id="42f70-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="42f70-105">\<bindings></span></span>  
<span data-ttu-id="42f70-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="42f70-106">\<customBinding></span></span>  
<span data-ttu-id="42f70-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="42f70-107">\<binding></span></span>  
<span data-ttu-id="42f70-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="42f70-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f70-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42f70-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42f70-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="42f70-110">Attributes and Elements</span></span>  
 <span data-ttu-id="42f70-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42f70-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42f70-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="42f70-112">Attributes</span></span>  
  
|<span data-ttu-id="42f70-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42f70-113">Attribute</span></span>|<span data-ttu-id="42f70-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42f70-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42f70-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="42f70-115">requireClientCertificate</span></span>|<span data-ttu-id="42f70-116">Bir istemci sertifikasının Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="42f70-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="42f70-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="42f70-117">The default is `false`.</span></span>|  
|<span data-ttu-id="42f70-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="42f70-118">sslProtocols</span></span>|<span data-ttu-id="42f70-119">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="42f70-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="42f70-120">Ssl3 varsayılandır&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="42f70-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42f70-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="42f70-121">Child Elements</span></span>  
 <span data-ttu-id="42f70-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="42f70-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42f70-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="42f70-123">Parent Elements</span></span>  
  
|<span data-ttu-id="42f70-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="42f70-124">Element</span></span>|<span data-ttu-id="42f70-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42f70-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42f70-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="42f70-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="42f70-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="42f70-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42f70-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42f70-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="42f70-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="42f70-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42f70-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="42f70-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="42f70-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="42f70-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="42f70-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="42f70-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
