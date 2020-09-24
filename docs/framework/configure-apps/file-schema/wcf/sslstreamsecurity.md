---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: aa6bc7f5a94afc8a190d3d9d2d71ea8b38d8c25b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153579"
---
# \<sslStreamSecurity>

<span data-ttu-id="5af98-101">SSL akışı kullanarak kanal güvenliğini destekleyen bir özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5af98-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="5af98-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="5af98-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5af98-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af98-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5af98-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5af98-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5af98-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5af98-105">Attributes</span></span>  
  
|<span data-ttu-id="5af98-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5af98-106">Attribute</span></span>|<span data-ttu-id="5af98-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af98-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5af98-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5af98-108">requireClientCertificate</span></span>|<span data-ttu-id="5af98-109">Bu bağlama için bir istemci sertifikasının gerekli olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="5af98-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="5af98-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="5af98-110">The default is `false`.</span></span>|  
|<span data-ttu-id="5af98-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5af98-111">sslProtocols</span></span>|<span data-ttu-id="5af98-112">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="5af98-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5af98-113">Varsayılan, Ssl3&#124;TLS&#124;Tls11&#124;Tls12 'dir.</span><span class="sxs-lookup"><span data-stu-id="5af98-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5af98-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af98-114">Child Elements</span></span>  

 <span data-ttu-id="5af98-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="5af98-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5af98-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af98-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5af98-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5af98-117">Element</span></span>|<span data-ttu-id="5af98-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af98-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5af98-119">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5af98-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5af98-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5af98-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="5af98-121">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5af98-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5af98-122">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5af98-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5af98-123">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5af98-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
