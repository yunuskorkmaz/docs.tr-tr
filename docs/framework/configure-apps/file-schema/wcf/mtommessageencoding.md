---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 70a124fda5bc0e52e1271716f7e2166b7717b49a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933199"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="e9732-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="e9732-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="e9732-102">SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9732-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="e9732-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9732-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e9732-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e9732-104">\<bindings></span></span>  
<span data-ttu-id="e9732-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e9732-105">\<customBinding></span></span>  
<span data-ttu-id="e9732-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e9732-106">\<binding></span></span>  
<span data-ttu-id="e9732-107">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="e9732-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9732-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9732-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9732-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9732-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9732-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9732-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9732-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9732-111">Attributes</span></span>  
  
|<span data-ttu-id="e9732-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e9732-112">Attribute</span></span>|<span data-ttu-id="e9732-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9732-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9732-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="e9732-114">maxBufferSize</span></span>|<span data-ttu-id="e9732-115">Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9732-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="e9732-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e9732-116">maxReadPoolSize</span></span>|<span data-ttu-id="e9732-117">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9732-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="e9732-118">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e9732-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e9732-119">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e9732-119">The default is 64.</span></span>|  
|<span data-ttu-id="e9732-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e9732-120">maxWritePoolSize</span></span>|<span data-ttu-id="e9732-121">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9732-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="e9732-122">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e9732-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e9732-123">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="e9732-123">The default is 16.</span></span>|  
|<span data-ttu-id="e9732-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="e9732-124">messageVersion</span></span>|<span data-ttu-id="e9732-125">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9732-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="e9732-126">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="e9732-126">Valid values are</span></span><br /><br /> <span data-ttu-id="e9732-127">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="e9732-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="e9732-128">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="e9732-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="e9732-129">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e9732-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="e9732-130">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="e9732-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="e9732-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="e9732-131">writeEncoding</span></span>|<span data-ttu-id="e9732-132">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9732-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e9732-133">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="e9732-133">Valid values are</span></span><br /><br /> <span data-ttu-id="e9732-134">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="e9732-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="e9732-135">- Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="e9732-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="e9732-136">- Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="e9732-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="e9732-137">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="e9732-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="e9732-138">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e9732-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9732-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9732-139">Child Elements</span></span>  
  
|<span data-ttu-id="e9732-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9732-140">Element</span></span>|<span data-ttu-id="e9732-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9732-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9732-142">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9732-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e9732-143">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9732-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e9732-144">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e9732-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9732-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9732-145">Parent Elements</span></span>  
  
|<span data-ttu-id="e9732-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9732-146">Element</span></span>|<span data-ttu-id="e9732-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9732-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9732-148">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e9732-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e9732-149">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9732-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9732-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9732-150">Remarks</span></span>  
 <span data-ttu-id="e9732-151">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="e9732-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="e9732-152">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="e9732-152">Decoding is the reverse process.</span></span> <span data-ttu-id="e9732-153">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: Metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="e9732-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="e9732-154">`MtomMessageEncoding` Öğesi, bir ileti iletimi iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9732-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="e9732-155">MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="e9732-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="e9732-156">MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9732-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="e9732-157">MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="e9732-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9732-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9732-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="e9732-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9732-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="e9732-160">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="e9732-160">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="e9732-161">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="e9732-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="e9732-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e9732-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9732-163">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="e9732-163">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e9732-164">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e9732-164">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e9732-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e9732-165">\<customBinding></span></span>](custombinding.md)
