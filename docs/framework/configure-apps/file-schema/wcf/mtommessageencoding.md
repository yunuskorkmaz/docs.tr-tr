---
title: '&lt;mtomMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 237891b5f855707f40f4fb58c08b80daa24f4def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="af936-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="af936-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="af936-103">SOAP iletisi iletim en iyi duruma getirme mekanizmasını (temel MTOM) iletiler için kullanılan kodlama ve ileti sürüm belirtir.</span><span class="sxs-lookup"><span data-stu-id="af936-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="af936-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="af936-104">\<system.serviceModel></span></span>  
<span data-ttu-id="af936-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="af936-105">\<bindings></span></span>  
<span data-ttu-id="af936-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="af936-106">\<customBinding></span></span>  
<span data-ttu-id="af936-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="af936-107">\<binding></span></span>  
<span data-ttu-id="af936-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="af936-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af936-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af936-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af936-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="af936-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af936-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af936-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af936-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="af936-112">Attributes</span></span>  
  
|<span data-ttu-id="af936-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="af936-113">Attribute</span></span>|<span data-ttu-id="af936-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af936-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af936-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="af936-115">maxBufferSize</span></span>|<span data-ttu-id="af936-116">Kullanılabilir arabelleğinin maksimum boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="af936-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="af936-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="af936-117">maxReadPoolSize</span></span>|<span data-ttu-id="af936-118">Kaç tane iletileri belirten bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af936-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="af936-119">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="af936-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="af936-120">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af936-120">The default is 64.</span></span>|  
|<span data-ttu-id="af936-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="af936-121">maxWritePoolSize</span></span>|<span data-ttu-id="af936-122">Kaç tane iletileri belirten bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="af936-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="af936-123">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="af936-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="af936-124">16 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af936-124">The default is 16.</span></span>|  
|<span data-ttu-id="af936-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="af936-125">messageVersion</span></span>|<span data-ttu-id="af936-126">Bağlama kullanılarak gönderilen iletileri SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="af936-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="af936-127">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="af936-127">Valid values are</span></span><br /><br /> <span data-ttu-id="af936-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="af936-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="af936-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="af936-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="af936-130">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af936-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="af936-131">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="af936-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="af936-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="af936-132">writeEncoding</span></span>|<span data-ttu-id="af936-133">Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="af936-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="af936-134">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="af936-134">Valid values are</span></span><br /><br /> <span data-ttu-id="af936-135">-UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="af936-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="af936-136">-Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="af936-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="af936-137">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="af936-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="af936-138">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af936-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="af936-139">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="af936-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af936-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="af936-140">Child Elements</span></span>  
  
|<span data-ttu-id="af936-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="af936-141">Element</span></span>|<span data-ttu-id="af936-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af936-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af936-143">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="af936-143">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="af936-144">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af936-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="af936-145">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="af936-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af936-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="af936-146">Parent Elements</span></span>  
  
|<span data-ttu-id="af936-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="af936-147">Element</span></span>|<span data-ttu-id="af936-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af936-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af936-149">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="af936-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="af936-150">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af936-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af936-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af936-151">Remarks</span></span>  
 <span data-ttu-id="af936-152">Kodlama bayt dizisi bir ileti dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="af936-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="af936-153">Kod çözme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="af936-153">Decoding is the reverse process.</span></span> <span data-ttu-id="af936-154">Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="af936-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="af936-155">`MtomMessageEncoding` Öğesi karakter kodlama ve ileti sürüm oluşturma ve bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama kullanılarak iletiler için kullanılan diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="af936-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="af936-156">MTOM WCF iletilerindeki ikili veri iletmek için verimli bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="af936-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="af936-157">MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="af936-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="af936-158">MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-base64 ile kodlanmış biçimlerini dönüştürme olmadan, ise.</span><span class="sxs-lookup"><span data-stu-id="af936-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af936-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="af936-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="af936-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af936-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="af936-161">İleti kodlama</span><span class="sxs-lookup"><span data-stu-id="af936-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="af936-162">İleti Kodlayıcı seçme</span><span class="sxs-lookup"><span data-stu-id="af936-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="af936-163">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="af936-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="af936-164">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="af936-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="af936-165">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="af936-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="af936-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="af936-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
