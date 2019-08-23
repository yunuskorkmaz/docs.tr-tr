---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 5ed87adfb3963513602844fc69afce8f7994fa8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932429"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="4fef7-101">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="4fef7-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="4fef7-102">SSL akışı kullanarak kanal güvenliğini destekleyen bir özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fef7-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="4fef7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4fef7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4fef7-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4fef7-104">\<bindings></span></span>  
<span data-ttu-id="4fef7-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4fef7-105">\<customBinding></span></span>  
<span data-ttu-id="4fef7-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4fef7-106">\<binding></span></span>  
<span data-ttu-id="4fef7-107">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="4fef7-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fef7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fef7-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fef7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fef7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4fef7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fef7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fef7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4fef7-111">Attributes</span></span>  
  
|<span data-ttu-id="4fef7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4fef7-112">Attribute</span></span>|<span data-ttu-id="4fef7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fef7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fef7-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="4fef7-114">requireClientCertificate</span></span>|<span data-ttu-id="4fef7-115">Bu bağlama için bir istemci sertifikasının gerekli olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="4fef7-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="4fef7-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4fef7-116">The default is `false`.</span></span>|  
|<span data-ttu-id="4fef7-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="4fef7-117">sslProtocols</span></span>|<span data-ttu-id="4fef7-118">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="4fef7-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="4fef7-119">Varsayılan değer Ssl3&#124;TLS&#124;Tls11&#124;Tls12 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4fef7-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fef7-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fef7-120">Child Elements</span></span>  
 <span data-ttu-id="4fef7-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="4fef7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fef7-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fef7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4fef7-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fef7-123">Element</span></span>|<span data-ttu-id="4fef7-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fef7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fef7-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4fef7-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4fef7-126">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4fef7-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fef7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fef7-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="4fef7-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4fef7-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4fef7-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4fef7-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4fef7-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4fef7-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4fef7-131">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4fef7-131">\<customBinding></span></span>](custombinding.md)
