---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204451"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="f448e-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="f448e-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="f448e-102">SSL akışı kullanarak kanal güvenliğini destekleyen özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f448e-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="f448e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f448e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f448e-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f448e-104">\<bindings></span></span>  
<span data-ttu-id="f448e-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f448e-105">\<customBinding></span></span>  
<span data-ttu-id="f448e-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f448e-106">\<binding></span></span>  
<span data-ttu-id="f448e-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="f448e-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f448e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f448e-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f448e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f448e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f448e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f448e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f448e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f448e-111">Attributes</span></span>  
  
|<span data-ttu-id="f448e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f448e-112">Attribute</span></span>|<span data-ttu-id="f448e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f448e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f448e-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="f448e-114">requireClientCertificate</span></span>|<span data-ttu-id="f448e-115">Bir istemci sertifikasının Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f448e-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="f448e-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f448e-116">The default is `false`.</span></span>|  
|<span data-ttu-id="f448e-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="f448e-117">sslProtocols</span></span>|<span data-ttu-id="f448e-118">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f448e-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="f448e-119">Ssl3 varsayılandır&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="f448e-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f448e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f448e-120">Child Elements</span></span>  
 <span data-ttu-id="f448e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="f448e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f448e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f448e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f448e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f448e-123">Element</span></span>|<span data-ttu-id="f448e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f448e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f448e-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f448e-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f448e-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f448e-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f448e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f448e-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="f448e-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f448e-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f448e-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f448e-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f448e-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f448e-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f448e-131">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f448e-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
