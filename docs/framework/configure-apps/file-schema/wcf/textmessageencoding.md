---
title: '&lt;textMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ac17ead3c7054f0125527e3992fe865624770a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="a9439-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="a9439-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="a9439-103">Karakter kodlama ve sürüm oluşturma metin tabanlı XML iletileri için kullanılan ileti belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9439-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="a9439-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a9439-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a9439-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a9439-105">\<bindings></span></span>  
<span data-ttu-id="a9439-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a9439-106">\<customBinding></span></span>  
<span data-ttu-id="a9439-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a9439-107">\<binding></span></span>  
<span data-ttu-id="a9439-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="a9439-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9439-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9439-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9439-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9439-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a9439-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9439-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9439-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9439-112">Attributes</span></span>  
  
|<span data-ttu-id="a9439-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9439-113">Attribute</span></span>|<span data-ttu-id="a9439-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9439-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9439-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a9439-115">maxReadPoolSize</span></span>|<span data-ttu-id="a9439-116">Kaç tane iletileri belirten bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9439-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a9439-117">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="a9439-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a9439-118">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a9439-118">The default is 64.</span></span>|  
|<span data-ttu-id="a9439-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a9439-119">maxWritePoolSize</span></span>|<span data-ttu-id="a9439-120">Kaç tane iletileri belirten bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9439-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a9439-121">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="a9439-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a9439-122">16 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a9439-122">The default is 16.</span></span>|  
|<span data-ttu-id="a9439-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a9439-123">messageVersion</span></span>|<span data-ttu-id="a9439-124">Bağlama kullanılarak gönderilen iletileri SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9439-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="a9439-125">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="a9439-125">Valid values are</span></span><br /><br /> <span data-ttu-id="a9439-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="a9439-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="a9439-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="a9439-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="a9439-128">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a9439-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="a9439-129">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="a9439-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="a9439-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="a9439-130">writeEncoding</span></span>|<span data-ttu-id="a9439-131">Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9439-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a9439-132">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="a9439-132">Valid values are</span></span><br /><br /> <span data-ttu-id="a9439-133">-UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="a9439-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="a9439-134">-Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="a9439-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="a9439-135">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="a9439-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a9439-136">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a9439-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="a9439-137">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a9439-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9439-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9439-138">Child Elements</span></span>  
  
|<span data-ttu-id="a9439-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9439-139">Element</span></span>|<span data-ttu-id="a9439-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9439-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9439-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="a9439-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="a9439-142">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9439-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a9439-143">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a9439-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9439-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9439-144">Parent Elements</span></span>  
  
|<span data-ttu-id="a9439-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9439-145">Element</span></span>|<span data-ttu-id="a9439-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9439-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9439-147">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a9439-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a9439-148">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9439-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9439-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9439-149">Remarks</span></span>  
 <span data-ttu-id="a9439-150">Kodlama bayt dizisi bir ileti dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a9439-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a9439-151">Kod çözme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="a9439-151">Decoding is the reverse process.</span></span> <span data-ttu-id="a9439-152">Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a9439-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a9439-153">Metin kodlaması tarafından temsil edilen `textMessageEncoding` öğesidir en birlikte çalışabilir, ancak XML iletileri için az verimli Kodlayıcı.</span><span class="sxs-lookup"><span data-stu-id="a9439-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="a9439-154">Metin Kodlayıcı kablo metin tabanlı iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9439-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="a9439-155">Bu Kodlayıcı tarafından üretilen iletileri WS - için uygun * birlikte çalışabilirliği tabanlı.</span><span class="sxs-lookup"><span data-stu-id="a9439-155">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="a9439-156">Genellikle Web hizmeti veya Web hizmeti istemcisi metinsel XML anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9439-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="a9439-157">Ancak, büyük metin olarak ikili veri blokları iletmek için XML iletileri kodlama az verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a9439-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9439-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9439-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9439-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9439-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="a9439-160">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="a9439-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="a9439-161">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="a9439-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="a9439-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9439-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a9439-163">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a9439-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a9439-164">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9439-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a9439-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a9439-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
