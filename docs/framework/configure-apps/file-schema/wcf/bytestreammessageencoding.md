---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 165bf4cd1c0c5c1a6adae91650d38984bc47ef6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="f6b2e-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="f6b2e-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="f6b2e-103">Bayt karakter kodlamasını belirtme seçeneği ile bir akış olarak kodlama iletiyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="f6b2e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f6b2e-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-105">\<bindings></span></span>  
<span data-ttu-id="f6b2e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-106">\<customBinding></span></span>  
<span data-ttu-id="f6b2e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-107">\<binding></span></span>  
<span data-ttu-id="f6b2e-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b2e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6b2e-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6b2e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6b2e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6b2e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6b2e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6b2e-112">Attributes</span></span>  
  
|<span data-ttu-id="f6b2e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6b2e-113">Attribute</span></span>|<span data-ttu-id="f6b2e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6b2e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6b2e-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="f6b2e-115">messageVersion</span></span>|<span data-ttu-id="f6b2e-116">Bağlama kullanılarak gönderilen iletileri SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="f6b2e-117">Bu özellik yalnızca ileti sürümü değerine ayarlanabilir <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="f6b2e-118">Bayt akışı ileti Kodlayıcı diğer ileti sürümleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="f6b2e-119">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6b2e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6b2e-120">Child Elements</span></span>  
  
|<span data-ttu-id="f6b2e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6b2e-121">Element</span></span>|<span data-ttu-id="f6b2e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6b2e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6b2e-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f6b2e-124">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f6b2e-125">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6b2e-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6b2e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f6b2e-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6b2e-127">Element</span></span>|<span data-ttu-id="f6b2e-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6b2e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6b2e-129">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f6b2e-130">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6b2e-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6b2e-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="f6b2e-132">İleti kodlama</span><span class="sxs-lookup"><span data-stu-id="f6b2e-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="f6b2e-133">İleti Kodlayıcı seçme</span><span class="sxs-lookup"><span data-stu-id="f6b2e-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="f6b2e-134">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="f6b2e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6b2e-135">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="f6b2e-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f6b2e-136">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f6b2e-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f6b2e-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f6b2e-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
