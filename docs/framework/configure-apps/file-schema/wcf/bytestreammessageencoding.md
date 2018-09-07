---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 4b031bfb0d0979dc99df13c104a712d6dd771e8a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44059995"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="39a6c-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="39a6c-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="39a6c-103">Bir karakter kodlamasını belirtmek için seçeneği ile bayt akışı olarak kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39a6c-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="39a6c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="39a6c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39a6c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="39a6c-105">\<bindings></span></span>  
<span data-ttu-id="39a6c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="39a6c-106">\<customBinding></span></span>  
<span data-ttu-id="39a6c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="39a6c-107">\<binding></span></span>  
<span data-ttu-id="39a6c-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="39a6c-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a6c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39a6c-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39a6c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a6c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39a6c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39a6c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39a6c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39a6c-112">Attributes</span></span>  
  
|<span data-ttu-id="39a6c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39a6c-113">Attribute</span></span>|<span data-ttu-id="39a6c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a6c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39a6c-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="39a6c-115">messageVersion</span></span>|<span data-ttu-id="39a6c-116">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="39a6c-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="39a6c-117">Bu özellik yalnızca ileti sürümü değeri için ayarlanabilir <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="39a6c-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="39a6c-118">Bayt akışı ileti Kodlayıcı herhangi bir ileti sürümlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="39a6c-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="39a6c-119">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="39a6c-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39a6c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a6c-120">Child Elements</span></span>  
  
|<span data-ttu-id="39a6c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="39a6c-121">Element</span></span>|<span data-ttu-id="39a6c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a6c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39a6c-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="39a6c-123">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="39a6c-124">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39a6c-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="39a6c-125">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="39a6c-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39a6c-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a6c-126">Parent Elements</span></span>  
  
|<span data-ttu-id="39a6c-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="39a6c-127">Element</span></span>|<span data-ttu-id="39a6c-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a6c-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39a6c-129">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="39a6c-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="39a6c-130">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39a6c-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39a6c-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39a6c-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="39a6c-132">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="39a6c-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="39a6c-133">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="39a6c-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="39a6c-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="39a6c-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="39a6c-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="39a6c-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="39a6c-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="39a6c-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="39a6c-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="39a6c-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
