---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738598"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="8184d-101">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="8184d-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="8184d-102">SSL akışı kullanarak kanal güvenliğini destekleyen bir özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8184d-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="8184d-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8184d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8184d-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8184d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8184d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8184d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8184d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="8184d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="8184d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="8184d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8184d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="8184d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8184d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8184d-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8184d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8184d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8184d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8184d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8184d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8184d-112">Attributes</span></span>  
  
|<span data-ttu-id="8184d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8184d-113">Attribute</span></span>|<span data-ttu-id="8184d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8184d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8184d-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="8184d-115">requireClientCertificate</span></span>|<span data-ttu-id="8184d-116">Bu bağlama için bir istemci sertifikasının gerekli olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="8184d-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="8184d-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8184d-117">The default is `false`.</span></span>|  
|<span data-ttu-id="8184d-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="8184d-118">sslProtocols</span></span>|<span data-ttu-id="8184d-119">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="8184d-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="8184d-120">Varsayılan değer Ssl3&#124;TLS&#124;Tls11&#124;Tls12 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8184d-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8184d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8184d-121">Child Elements</span></span>  
 <span data-ttu-id="8184d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="8184d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8184d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8184d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8184d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="8184d-124">Element</span></span>|<span data-ttu-id="8184d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8184d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8184d-126">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="8184d-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="8184d-127">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8184d-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8184d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8184d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="8184d-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8184d-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8184d-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8184d-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8184d-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8184d-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8184d-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8184d-132">\<customBinding></span></span>](custombinding.md)
