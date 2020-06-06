---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739067"
---
# \<byteStreamMessageEncoding>
<span data-ttu-id="8fc8f-101">Karakter kodlamasını belirtme seçeneğiyle birlikte ileti kodlamasını bayt akışı olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-101">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="8fc8f-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fc8f-102">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fc8f-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fc8f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8fc8f-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fc8f-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8fc8f-105">Attributes</span></span>  
  
|<span data-ttu-id="8fc8f-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8fc8f-106">Attribute</span></span>|<span data-ttu-id="8fc8f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc8f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fc8f-108">messageVersion</span><span class="sxs-lookup"><span data-stu-id="8fc8f-108">messageVersion</span></span>|<span data-ttu-id="8fc8f-109">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-109">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="8fc8f-110">Bu özellik yalnızca ileti sürümü değerine ayarlanabilir <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="8fc8f-110">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="8fc8f-111">Bayt akışı ileti Kodlayıcısı diğer herhangi bir ileti sürümünü desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-111">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="8fc8f-112">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="8fc8f-112">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fc8f-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fc8f-113">Child Elements</span></span>  
  
|<span data-ttu-id="8fc8f-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fc8f-114">Element</span></span>|<span data-ttu-id="8fc8f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc8f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="8fc8f-116">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-116">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8fc8f-117">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="8fc8f-117">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fc8f-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fc8f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8fc8f-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fc8f-119">Element</span></span>|<span data-ttu-id="8fc8f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc8f-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8fc8f-121">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fc8f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc8f-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="8fc8f-123">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="8fc8f-123">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="8fc8f-124">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="8fc8f-124">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="8fc8f-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8fc8f-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8fc8f-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8fc8f-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8fc8f-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8fc8f-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
