---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: fe633aa1ed2b165a83f415748b70b6a66bbb0130
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540929"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="5c13e-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="5c13e-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="5c13e-103">SSL akışı kullanarak kanal güvenliğini destekleyen özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c13e-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="5c13e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5c13e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5c13e-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="5c13e-105">\<bindings></span></span>  
<span data-ttu-id="5c13e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5c13e-106">\<customBinding></span></span>  
<span data-ttu-id="5c13e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5c13e-107">\<binding></span></span>  
<span data-ttu-id="5c13e-108">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="5c13e-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c13e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c13e-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c13e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c13e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5c13e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c13e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c13e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c13e-112">Attributes</span></span>  
  
|<span data-ttu-id="5c13e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c13e-113">Attribute</span></span>|<span data-ttu-id="5c13e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c13e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c13e-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5c13e-115">requireClientCertificate</span></span>|<span data-ttu-id="5c13e-116">Bir istemci sertifikasının Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5c13e-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="5c13e-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-117">The default is `false`.</span></span>|  
|<span data-ttu-id="5c13e-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5c13e-118">sslProtocols</span></span>|<span data-ttu-id="5c13e-119">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5c13e-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5c13e-120">Ssl3 varsayılandır&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="5c13e-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c13e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c13e-121">Child Elements</span></span>  
 <span data-ttu-id="5c13e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c13e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c13e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c13e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5c13e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c13e-124">Element</span></span>|<span data-ttu-id="5c13e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c13e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c13e-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5c13e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5c13e-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5c13e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c13e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c13e-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="5c13e-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5c13e-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="5c13e-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5c13e-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5c13e-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5c13e-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5c13e-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5c13e-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
