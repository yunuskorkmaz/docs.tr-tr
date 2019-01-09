---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: b081a577280f4f2a52ef3b5ece76f519f9701faa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145113"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="83ca1-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="83ca1-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="83ca1-103">SSL akışı kullanarak kanal güvenliğini destekleyen özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="83ca1-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="83ca1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="83ca1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="83ca1-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="83ca1-105">\<bindings></span></span>  
<span data-ttu-id="83ca1-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83ca1-106">\<customBinding></span></span>  
<span data-ttu-id="83ca1-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="83ca1-107">\<binding></span></span>  
<span data-ttu-id="83ca1-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="83ca1-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ca1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83ca1-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83ca1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83ca1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83ca1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83ca1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83ca1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83ca1-112">Attributes</span></span>  
  
|<span data-ttu-id="83ca1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83ca1-113">Attribute</span></span>|<span data-ttu-id="83ca1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83ca1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83ca1-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="83ca1-115">requireClientCertificate</span></span>|<span data-ttu-id="83ca1-116">Bir istemci sertifikasının Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="83ca1-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="83ca1-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="83ca1-117">The default is `false`.</span></span>|  
|<span data-ttu-id="83ca1-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="83ca1-118">sslProtocols</span></span>|<span data-ttu-id="83ca1-119">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="83ca1-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="83ca1-120">Ssl3 varsayılandır&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="83ca1-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83ca1-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83ca1-121">Child Elements</span></span>  
 <span data-ttu-id="83ca1-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="83ca1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83ca1-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83ca1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="83ca1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="83ca1-124">Element</span></span>|<span data-ttu-id="83ca1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83ca1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83ca1-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="83ca1-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="83ca1-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83ca1-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83ca1-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83ca1-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="83ca1-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="83ca1-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="83ca1-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="83ca1-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="83ca1-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="83ca1-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="83ca1-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83ca1-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
