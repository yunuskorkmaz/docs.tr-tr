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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1788300407ad84a5ff7e3929eaa728f5399961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="3504b-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="3504b-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="3504b-103">Bayt karakter kodlamasını belirtme seçeneği ile bir akış olarak kodlama iletiyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3504b-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="3504b-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3504b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3504b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3504b-105">\<bindings></span></span>  
<span data-ttu-id="3504b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3504b-106">\<customBinding></span></span>  
<span data-ttu-id="3504b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3504b-107">\<binding></span></span>  
<span data-ttu-id="3504b-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="3504b-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3504b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3504b-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3504b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3504b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3504b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3504b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3504b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3504b-112">Attributes</span></span>  
  
|<span data-ttu-id="3504b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3504b-113">Attribute</span></span>|<span data-ttu-id="3504b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3504b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3504b-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3504b-115">messageVersion</span></span>|<span data-ttu-id="3504b-116">Bağlama kullanılarak gönderilen iletileri SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3504b-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3504b-117">Bu özellik yalnızca ileti sürümü değerine ayarlanabilir <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="3504b-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="3504b-118">Bayt akışı ileti Kodlayıcı diğer ileti sürümleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3504b-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="3504b-119">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="3504b-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3504b-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3504b-120">Child Elements</span></span>  
  
|<span data-ttu-id="3504b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="3504b-121">Element</span></span>|<span data-ttu-id="3504b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3504b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3504b-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="3504b-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="3504b-124">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3504b-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3504b-125">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="3504b-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3504b-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3504b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3504b-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="3504b-127">Element</span></span>|<span data-ttu-id="3504b-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3504b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3504b-129">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3504b-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3504b-130">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3504b-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3504b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3504b-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="3504b-132">İleti kodlama</span><span class="sxs-lookup"><span data-stu-id="3504b-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="3504b-133">İleti Kodlayıcı seçme</span><span class="sxs-lookup"><span data-stu-id="3504b-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="3504b-134">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="3504b-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3504b-135">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="3504b-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3504b-136">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3504b-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3504b-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3504b-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
