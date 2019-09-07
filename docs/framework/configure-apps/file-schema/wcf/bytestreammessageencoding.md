---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 5d78aed78a5c3a10aecac53bda02d6c640bc71ae
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400578"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="fddd9-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="fddd9-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="fddd9-102">Karakter kodlamasını belirtme seçeneğiyle birlikte ileti kodlamasını bayt akışı olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="fddd9-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="fddd9-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fddd9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fddd9-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fddd9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fddd9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fddd9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="fddd9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="fddd9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="fddd9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="fddd9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="fddd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="fddd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fddd9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fddd9-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fddd9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fddd9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fddd9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fddd9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fddd9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fddd9-112">Attributes</span></span>  
  
|<span data-ttu-id="fddd9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fddd9-113">Attribute</span></span>|<span data-ttu-id="fddd9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fddd9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fddd9-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="fddd9-115">messageVersion</span></span>|<span data-ttu-id="fddd9-116">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fddd9-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="fddd9-117">Bu özellik yalnızca ileti sürümü değerine <xref:System.ServiceModel.Channels.MessageVersion.None%2A>ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fddd9-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="fddd9-118">Bayt akışı ileti Kodlayıcısı diğer herhangi bir ileti sürümünü desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fddd9-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="fddd9-119">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="fddd9-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fddd9-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fddd9-120">Child Elements</span></span>  
  
|<span data-ttu-id="fddd9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fddd9-121">Element</span></span>|<span data-ttu-id="fddd9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fddd9-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fddd9-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fddd9-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="fddd9-124">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fddd9-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fddd9-125">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fddd9-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fddd9-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fddd9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fddd9-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fddd9-127">Element</span></span>|<span data-ttu-id="fddd9-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fddd9-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fddd9-129">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fddd9-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="fddd9-130">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fddd9-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fddd9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fddd9-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="fddd9-132">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="fddd9-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="fddd9-133">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="fddd9-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="fddd9-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fddd9-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fddd9-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="fddd9-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fddd9-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fddd9-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fddd9-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fddd9-137">\<customBinding></span></span>](custombinding.md)
