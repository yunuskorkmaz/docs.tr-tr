---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e1314347dfb83fb0631ebaa98b4d35bb0ac402f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="6c0d3-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="6c0d3-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="6c0d3-103">Windows Communication Foundation (WCF) iletilerinde hattaki ikili kodlar bir ikili ileti Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="6c0d3-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6c0d3-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-105">\<bindings></span></span>  
<span data-ttu-id="6c0d3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-106">\<customBinding></span></span>  
<span data-ttu-id="6c0d3-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-107">\<binding></span></span>  
<span data-ttu-id="6c0d3-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0d3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c0d3-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c0d3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c0d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6c0d3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c0d3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c0d3-112">Attributes</span></span>  
  
|<span data-ttu-id="6c0d3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c0d3-113">Attribute</span></span>|<span data-ttu-id="6c0d3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c0d3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c0d3-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="6c0d3-115">maxReadPoolSize</span></span>|<span data-ttu-id="6c0d3-116">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="6c0d3-117">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="6c0d3-118">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-118">The default is 64.</span></span>|  
|<span data-ttu-id="6c0d3-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="6c0d3-119">maxSessionSize</span></span>|<span data-ttu-id="6c0d3-120">Kodlama için kullanılan arabelleğin bayt cinsinden boyutu ayarlar pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="6c0d3-121">Daha büyük bir arabellek çalışma kümesi boyutu ödün verme pahasına kodlama hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="6c0d3-122">Varsayılan 2048'dir.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-122">The default is 2048.</span></span>|  
|<span data-ttu-id="6c0d3-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="6c0d3-123">maxWritePoolSize</span></span>|<span data-ttu-id="6c0d3-124">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="6c0d3-125">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="6c0d3-126">16 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-126">The default is 16.</span></span>|  
|<span data-ttu-id="6c0d3-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="6c0d3-127">messageVersion</span></span>|<span data-ttu-id="6c0d3-128">SOAP iletisi ve beklenmeyen veya kullanılan WS adresleme sürümleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c0d3-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c0d3-129">Child Elements</span></span>  
  
|<span data-ttu-id="6c0d3-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c0d3-130">Element</span></span>|<span data-ttu-id="6c0d3-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c0d3-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c0d3-132">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-132">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="6c0d3-133">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6c0d3-134">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c0d3-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c0d3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6c0d3-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c0d3-136">Element</span></span>|<span data-ttu-id="6c0d3-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c0d3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c0d3-138">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6c0d3-139">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c0d3-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c0d3-140">Remarks</span></span>  
 <span data-ttu-id="6c0d3-141">Kodlama bayt dizisi bir ileti dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="6c0d3-142">Kod çözme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-142">Decoding is the reverse process.</span></span> <span data-ttu-id="6c0d3-143">Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="6c0d3-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="6c0d3-144">`binaryMessageEncoding` Öğesi için XML .NET ikili biçimini belirtir ve karakter kodlamasını belirtmek için seçenekler ve kullanılacak SOAP ve WS adresleme sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="6c0d3-145">İkili ileti Kodlayıcı ikili hat üzerinde Windows Communication Foundation (WCF) iletilerinde kodlar.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="6c0d3-146">Bu kodlama ileti çok hızlı aktarımını sonuçları, birlikte çalışabilirlik tabanlı WS - üzerinde * standartları kaybolur.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c0d3-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c0d3-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c0d3-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="6c0d3-149">İleti kodlama</span><span class="sxs-lookup"><span data-stu-id="6c0d3-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="6c0d3-150">İleti Kodlayıcı seçme</span><span class="sxs-lookup"><span data-stu-id="6c0d3-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="6c0d3-151">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="6c0d3-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6c0d3-152">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="6c0d3-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6c0d3-153">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6c0d3-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6c0d3-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6c0d3-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
