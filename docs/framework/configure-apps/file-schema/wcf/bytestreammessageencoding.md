---
description: 'Hakkında daha fazla bilgi edinin: <byteStreamMessageEncoding>'
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 9cbb4eacb1a960481ee262db662160b5a342e27f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639295"
---
# \<byteStreamMessageEncoding>

<span data-ttu-id="d50b6-102">Karakter kodlamasını belirtme seçeneğiyle birlikte ileti kodlamasını bayt akışı olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="d50b6-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="d50b6-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="d50b6-103">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d50b6-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d50b6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d50b6-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d50b6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d50b6-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d50b6-106">Attributes</span></span>  
  
|<span data-ttu-id="d50b6-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d50b6-107">Attribute</span></span>|<span data-ttu-id="d50b6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50b6-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d50b6-109">messageVersion</span><span class="sxs-lookup"><span data-stu-id="d50b6-109">messageVersion</span></span>|<span data-ttu-id="d50b6-110">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d50b6-110">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="d50b6-111">Bu özellik yalnızca ileti sürümü değerine ayarlanabilir <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="d50b6-111">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="d50b6-112">Bayt akışı ileti Kodlayıcısı diğer herhangi bir ileti sürümünü desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d50b6-112">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="d50b6-113">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="d50b6-113">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d50b6-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d50b6-114">Child Elements</span></span>  
  
|<span data-ttu-id="d50b6-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d50b6-115">Element</span></span>|<span data-ttu-id="d50b6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50b6-116">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="d50b6-117">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d50b6-117">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d50b6-118">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="d50b6-118">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d50b6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d50b6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d50b6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="d50b6-120">Element</span></span>|<span data-ttu-id="d50b6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50b6-121">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d50b6-122">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d50b6-122">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d50b6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d50b6-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="d50b6-124">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="d50b6-124">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="d50b6-125">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="d50b6-125">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="d50b6-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d50b6-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d50b6-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="d50b6-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d50b6-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d50b6-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
