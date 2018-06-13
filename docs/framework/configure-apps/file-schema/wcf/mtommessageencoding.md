---
title: '&lt;mtomMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 25990e5583ba1daca378af40e7e56953c95b4a66
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746832"
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="cb4fd-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="cb4fd-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="cb4fd-103">SOAP iletisi iletim en iyi duruma getirme mekanizmasını (temel MTOM) iletiler için kullanılan kodlama ve ileti sürüm belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="cb4fd-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cb4fd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cb4fd-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-105">\<bindings></span></span>  
<span data-ttu-id="cb4fd-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-106">\<customBinding></span></span>  
<span data-ttu-id="cb4fd-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-107">\<binding></span></span>  
<span data-ttu-id="cb4fd-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb4fd-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb4fd-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb4fd-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb4fd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cb4fd-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb4fd-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb4fd-112">Attributes</span></span>  
  
|<span data-ttu-id="cb4fd-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb4fd-113">Attribute</span></span>|<span data-ttu-id="cb4fd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb4fd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb4fd-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="cb4fd-115">maxBufferSize</span></span>|<span data-ttu-id="cb4fd-116">Kullanılabilir arabelleğinin maksimum boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="cb4fd-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="cb4fd-117">maxReadPoolSize</span></span>|<span data-ttu-id="cb4fd-118">Kaç tane iletileri belirten bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="cb4fd-119">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cb4fd-120">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-120">The default is 64.</span></span>|  
|<span data-ttu-id="cb4fd-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="cb4fd-121">maxWritePoolSize</span></span>|<span data-ttu-id="cb4fd-122">Kaç tane iletileri belirten bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="cb4fd-123">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cb4fd-124">16 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-124">The default is 16.</span></span>|  
|<span data-ttu-id="cb4fd-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="cb4fd-125">messageVersion</span></span>|<span data-ttu-id="cb4fd-126">Bağlama kullanılarak gönderilen iletileri SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="cb4fd-127">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="cb4fd-127">Valid values are</span></span><br /><br /> <span data-ttu-id="cb4fd-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="cb4fd-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="cb4fd-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="cb4fd-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="cb4fd-130">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="cb4fd-131">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="cb4fd-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="cb4fd-132">writeEncoding</span></span>|<span data-ttu-id="cb4fd-133">Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="cb4fd-134">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="cb4fd-134">Valid values are</span></span><br /><br /> <span data-ttu-id="cb4fd-135">-UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="cb4fd-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="cb4fd-136">-Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="cb4fd-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="cb4fd-137">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="cb4fd-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="cb4fd-138">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="cb4fd-139">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb4fd-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb4fd-140">Child Elements</span></span>  
  
|<span data-ttu-id="cb4fd-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb4fd-141">Element</span></span>|<span data-ttu-id="cb4fd-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb4fd-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb4fd-143">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-143">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="cb4fd-144">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="cb4fd-145">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb4fd-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb4fd-146">Parent Elements</span></span>  
  
|<span data-ttu-id="cb4fd-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb4fd-147">Element</span></span>|<span data-ttu-id="cb4fd-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb4fd-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb4fd-149">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="cb4fd-150">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb4fd-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb4fd-151">Remarks</span></span>  
 <span data-ttu-id="cb4fd-152">Kodlama bayt dizisi bir ileti dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="cb4fd-153">Kod çözme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-153">Decoding is the reverse process.</span></span> <span data-ttu-id="cb4fd-154">Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="cb4fd-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="cb4fd-155">`MtomMessageEncoding` Öğesi karakter kodlama ve ileti sürüm oluşturma ve bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama kullanılarak iletiler için kullanılan diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="cb4fd-156">MTOM WCF iletilerindeki ikili veri iletmek için verimli bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="cb4fd-157">MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="cb4fd-158">MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-base64 ile kodlanmış biçimlerini dönüştürme olmadan, ise.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb4fd-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb4fd-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb4fd-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb4fd-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="cb4fd-161">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="cb4fd-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="cb4fd-162">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="cb4fd-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="cb4fd-163">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb4fd-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cb4fd-164">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="cb4fd-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cb4fd-165">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb4fd-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cb4fd-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb4fd-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
