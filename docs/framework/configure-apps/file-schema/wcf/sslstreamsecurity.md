---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
ms.openlocfilehash: 6eacf1833ecf980696d75c5dbcaaba3ba6403d92
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087456"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="d069d-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="d069d-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="d069d-103">SSL akışı kullanarak kanal güvenliğini destekleyen özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d069d-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="d069d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d069d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d069d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d069d-105">\<bindings></span></span>  
<span data-ttu-id="d069d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d069d-106">\<customBinding></span></span>  
<span data-ttu-id="d069d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d069d-107">\<binding></span></span>  
<span data-ttu-id="d069d-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="d069d-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d069d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d069d-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d069d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d069d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d069d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d069d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d069d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d069d-112">Attributes</span></span>  
  
|<span data-ttu-id="d069d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d069d-113">Attribute</span></span>|<span data-ttu-id="d069d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d069d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d069d-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="d069d-115">requireClientCertificate</span></span>|<span data-ttu-id="d069d-116">Bir istemci sertifikasının Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d069d-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="d069d-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d069d-117">The default is `false`.</span></span>|  
|<span data-ttu-id="d069d-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="d069d-118">sslProtocols</span></span>|<span data-ttu-id="d069d-119">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d069d-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="d069d-120">Ssl3 varsayılandır&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="d069d-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d069d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d069d-121">Child Elements</span></span>  
 <span data-ttu-id="d069d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d069d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d069d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d069d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d069d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d069d-124">Element</span></span>|<span data-ttu-id="d069d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d069d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d069d-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d069d-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d069d-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d069d-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d069d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d069d-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="d069d-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d069d-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d069d-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="d069d-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d069d-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d069d-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d069d-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d069d-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
