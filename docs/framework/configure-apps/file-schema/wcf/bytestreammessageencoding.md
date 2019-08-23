---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: b11f472c0e33003e50be4b45bb49196c64ecb70d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919724"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="71ca7-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="71ca7-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="71ca7-102">Karakter kodlamasını belirtme seçeneğiyle birlikte ileti kodlamasını bayt akışı olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="71ca7-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="71ca7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="71ca7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="71ca7-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="71ca7-104">\<bindings></span></span>  
<span data-ttu-id="71ca7-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="71ca7-105">\<customBinding></span></span>  
<span data-ttu-id="71ca7-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="71ca7-106">\<binding></span></span>  
<span data-ttu-id="71ca7-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="71ca7-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ca7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71ca7-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71ca7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="71ca7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="71ca7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71ca7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71ca7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71ca7-111">Attributes</span></span>  
  
|<span data-ttu-id="71ca7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="71ca7-112">Attribute</span></span>|<span data-ttu-id="71ca7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71ca7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71ca7-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="71ca7-114">messageVersion</span></span>|<span data-ttu-id="71ca7-115">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="71ca7-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="71ca7-116">Bu özellik yalnızca ileti sürümü değerine <xref:System.ServiceModel.Channels.MessageVersion.None%2A>ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="71ca7-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="71ca7-117">Bayt akışı ileti Kodlayıcısı diğer herhangi bir ileti sürümünü desteklemez.</span><span class="sxs-lookup"><span data-stu-id="71ca7-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="71ca7-118">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="71ca7-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71ca7-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="71ca7-119">Child Elements</span></span>  
  
|<span data-ttu-id="71ca7-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="71ca7-120">Element</span></span>|<span data-ttu-id="71ca7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71ca7-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71ca7-122">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71ca7-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="71ca7-123">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71ca7-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="71ca7-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="71ca7-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71ca7-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="71ca7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="71ca7-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="71ca7-126">Element</span></span>|<span data-ttu-id="71ca7-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71ca7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71ca7-128">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="71ca7-128">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="71ca7-129">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71ca7-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71ca7-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71ca7-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="71ca7-131">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="71ca7-131">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="71ca7-132">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="71ca7-132">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="71ca7-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="71ca7-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="71ca7-134">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="71ca7-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="71ca7-135">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="71ca7-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="71ca7-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="71ca7-136">\<customBinding></span></span>](custombinding.md)
