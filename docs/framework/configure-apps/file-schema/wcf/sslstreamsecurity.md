---
description: 'Hakkında daha fazla bilgi edinin: <sslStreamSecurity>'
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 77e08deb5263e330ead5df21ed1ef2dddbba28ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682702"
---
# \<sslStreamSecurity>

<span data-ttu-id="e42ac-102">SSL akışı kullanarak kanal güvenliğini destekleyen bir özel bağlama öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e42ac-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="e42ac-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="e42ac-103">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e42ac-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e42ac-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e42ac-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e42ac-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e42ac-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e42ac-106">Attributes</span></span>  
  
|<span data-ttu-id="e42ac-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e42ac-107">Attribute</span></span>|<span data-ttu-id="e42ac-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42ac-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e42ac-109">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e42ac-109">requireClientCertificate</span></span>|<span data-ttu-id="e42ac-110">Bu bağlama için bir istemci sertifikasının gerekli olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="e42ac-110">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="e42ac-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="e42ac-111">The default is `false`.</span></span>|  
|<span data-ttu-id="e42ac-112">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="e42ac-112">sslProtocols</span></span>|<span data-ttu-id="e42ac-113">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="e42ac-113">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e42ac-114">Varsayılan, Ssl3&#124;TLS&#124;Tls11&#124;Tls12 'dir.</span><span class="sxs-lookup"><span data-stu-id="e42ac-114">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e42ac-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e42ac-115">Child Elements</span></span>  

 <span data-ttu-id="e42ac-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e42ac-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e42ac-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e42ac-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e42ac-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e42ac-118">Element</span></span>|<span data-ttu-id="e42ac-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42ac-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e42ac-120">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e42ac-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e42ac-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e42ac-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="e42ac-122">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e42ac-122">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e42ac-123">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="e42ac-123">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e42ac-124">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e42ac-124">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
