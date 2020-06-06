---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738598"
---
# \<sslStreamSecurity>
<span data-ttu-id="c2f80-101">SSL akışı kullanarak kanal güvenliğini destekleyen bir özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2f80-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="c2f80-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2f80-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2f80-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2f80-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c2f80-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2f80-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2f80-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2f80-105">Attributes</span></span>  
  
|<span data-ttu-id="c2f80-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c2f80-106">Attribute</span></span>|<span data-ttu-id="c2f80-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2f80-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2f80-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="c2f80-108">requireClientCertificate</span></span>|<span data-ttu-id="c2f80-109">Bu bağlama için bir istemci sertifikasının gerekli olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="c2f80-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="c2f80-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="c2f80-110">The default is `false`.</span></span>|  
|<span data-ttu-id="c2f80-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="c2f80-111">sslProtocols</span></span>|<span data-ttu-id="c2f80-112">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="c2f80-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="c2f80-113">Varsayılan, Ssl3&#124;TLS&#124;Tls11&#124;Tls12 'dir.</span><span class="sxs-lookup"><span data-stu-id="c2f80-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2f80-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2f80-114">Child Elements</span></span>  
 <span data-ttu-id="c2f80-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c2f80-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2f80-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2f80-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c2f80-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c2f80-117">Element</span></span>|<span data-ttu-id="c2f80-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2f80-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c2f80-119">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c2f80-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2f80-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f80-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="c2f80-121">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c2f80-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c2f80-122">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c2f80-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c2f80-123">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c2f80-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
