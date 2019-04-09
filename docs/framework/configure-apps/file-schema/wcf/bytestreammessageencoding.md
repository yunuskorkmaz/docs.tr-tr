---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: ce9f282ea1101befe3bf99762efa61e9b47b74cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109908"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="8cabd-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="8cabd-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="8cabd-102">Bir karakter kodlamasını belirtmek için seçeneği ile bayt akışı olarak kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8cabd-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="8cabd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8cabd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8cabd-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="8cabd-104">\<bindings></span></span>  
<span data-ttu-id="8cabd-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8cabd-105">\<customBinding></span></span>  
<span data-ttu-id="8cabd-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8cabd-106">\<binding></span></span>  
<span data-ttu-id="8cabd-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="8cabd-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cabd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8cabd-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cabd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8cabd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8cabd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8cabd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cabd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8cabd-111">Attributes</span></span>  
  
|<span data-ttu-id="8cabd-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8cabd-112">Attribute</span></span>|<span data-ttu-id="8cabd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cabd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cabd-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="8cabd-114">messageVersion</span></span>|<span data-ttu-id="8cabd-115">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8cabd-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="8cabd-116">Bu özellik yalnızca ileti sürümü değeri için ayarlanabilir <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cabd-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="8cabd-117">Bayt akışı ileti Kodlayıcı herhangi bir ileti sürümlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8cabd-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="8cabd-118">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="8cabd-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cabd-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8cabd-119">Child Elements</span></span>  
  
|<span data-ttu-id="8cabd-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8cabd-120">Element</span></span>|<span data-ttu-id="8cabd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cabd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cabd-122">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="8cabd-122">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="8cabd-123">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8cabd-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8cabd-124">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8cabd-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8cabd-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8cabd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8cabd-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="8cabd-126">Element</span></span>|<span data-ttu-id="8cabd-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cabd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cabd-128">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8cabd-128">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8cabd-129">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8cabd-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cabd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cabd-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="8cabd-131">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="8cabd-131">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="8cabd-132">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="8cabd-132">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="8cabd-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8cabd-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8cabd-134">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8cabd-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8cabd-135">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8cabd-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8cabd-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8cabd-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
