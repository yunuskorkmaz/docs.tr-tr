---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739067"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="27e17-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="27e17-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="27e17-102">Karakter kodlamasını belirtme seçeneğiyle birlikte ileti kodlamasını bayt akışı olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="27e17-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="27e17-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="27e17-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27e17-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="27e17-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27e17-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="27e17-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="27e17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="27e17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="27e17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="27e17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="27e17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="27e17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e17-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27e17-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27e17-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27e17-110">Attributes and Elements</span></span>  
 <span data-ttu-id="27e17-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27e17-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27e17-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27e17-112">Attributes</span></span>  
  
|<span data-ttu-id="27e17-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27e17-113">Attribute</span></span>|<span data-ttu-id="27e17-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27e17-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27e17-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="27e17-115">messageVersion</span></span>|<span data-ttu-id="27e17-116">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="27e17-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="27e17-117">Bu özellik yalnızca <xref:System.ServiceModel.Channels.MessageVersion.None%2A>ileti sürümü değerine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="27e17-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="27e17-118">Bayt akışı ileti Kodlayıcısı diğer herhangi bir ileti sürümünü desteklemez.</span><span class="sxs-lookup"><span data-stu-id="27e17-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="27e17-119">Bu öznitelik <xref:System.ServiceModel.Channels.MessageVersion>türündedir.</span><span class="sxs-lookup"><span data-stu-id="27e17-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27e17-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27e17-120">Child Elements</span></span>  
  
|<span data-ttu-id="27e17-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="27e17-121">Element</span></span>|<span data-ttu-id="27e17-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27e17-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27e17-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="27e17-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="27e17-124">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27e17-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="27e17-125">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="27e17-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27e17-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27e17-126">Parent Elements</span></span>  
  
|<span data-ttu-id="27e17-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="27e17-127">Element</span></span>|<span data-ttu-id="27e17-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27e17-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27e17-129">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="27e17-129">\<binding></span></span>](bindings.md)|<span data-ttu-id="27e17-130">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27e17-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27e17-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27e17-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="27e17-132">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="27e17-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="27e17-133">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="27e17-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="27e17-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="27e17-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="27e17-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="27e17-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="27e17-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="27e17-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="27e17-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="27e17-137">\<customBinding></span></span>](custombinding.md)
