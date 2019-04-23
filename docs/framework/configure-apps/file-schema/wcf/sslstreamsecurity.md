---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204451"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="c6da8-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="c6da8-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="c6da8-102">SSL akışı kullanarak kanal güvenliğini destekleyen özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6da8-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="c6da8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6da8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c6da8-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c6da8-104">\<bindings></span></span>  
<span data-ttu-id="c6da8-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6da8-105">\<customBinding></span></span>  
<span data-ttu-id="c6da8-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c6da8-106">\<binding></span></span>  
<span data-ttu-id="c6da8-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="c6da8-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6da8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6da8-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6da8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6da8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c6da8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6da8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6da8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6da8-111">Attributes</span></span>  
  
|<span data-ttu-id="c6da8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6da8-112">Attribute</span></span>|<span data-ttu-id="c6da8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6da8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6da8-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="c6da8-114">requireClientCertificate</span></span>|<span data-ttu-id="c6da8-115">Bir istemci sertifikasının Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c6da8-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="c6da8-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c6da8-116">The default is `false`.</span></span>|  
|<span data-ttu-id="c6da8-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="c6da8-117">sslProtocols</span></span>|<span data-ttu-id="c6da8-118">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c6da8-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="c6da8-119">Ssl3 varsayılandır&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="c6da8-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6da8-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6da8-120">Child Elements</span></span>  
 <span data-ttu-id="c6da8-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6da8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6da8-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6da8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c6da8-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6da8-123">Element</span></span>|<span data-ttu-id="c6da8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6da8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6da8-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c6da8-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c6da8-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6da8-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6da8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6da8-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="c6da8-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c6da8-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c6da8-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c6da8-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c6da8-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c6da8-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c6da8-131">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6da8-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
