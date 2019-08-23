---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e2fec2c2e5979b08ed0d832f636b3d0847b9a5dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915654"
---
# <a name="textmessageencoding"></a><span data-ttu-id="ee8e8-101">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-101">\<textMessageEncoding></span></span>
<span data-ttu-id="ee8e8-102">Metin tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="ee8e8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ee8e8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ee8e8-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-104">\<bindings></span></span>  
<span data-ttu-id="ee8e8-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-105">\<customBinding></span></span>  
<span data-ttu-id="ee8e8-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-106">\<binding></span></span>  
<span data-ttu-id="ee8e8-107">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee8e8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee8e8-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee8e8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee8e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ee8e8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee8e8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee8e8-111">Attributes</span></span>  
  
|<span data-ttu-id="ee8e8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ee8e8-112">Attribute</span></span>|<span data-ttu-id="ee8e8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee8e8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee8e8-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ee8e8-114">maxReadPoolSize</span></span>|<span data-ttu-id="ee8e8-115">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="ee8e8-116">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ee8e8-117">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-117">The default is 64.</span></span>|  
|<span data-ttu-id="ee8e8-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ee8e8-118">maxWritePoolSize</span></span>|<span data-ttu-id="ee8e8-119">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="ee8e8-120">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ee8e8-121">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-121">The default is 16.</span></span>|  
|<span data-ttu-id="ee8e8-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="ee8e8-122">messageVersion</span></span>|<span data-ttu-id="ee8e8-123">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="ee8e8-124">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="ee8e8-124">Valid values are</span></span><br /><br /> <span data-ttu-id="ee8e8-125">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="ee8e8-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="ee8e8-126">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="ee8e8-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="ee8e8-127">- Soap11</span><span class="sxs-lookup"><span data-stu-id="ee8e8-127">-   Soap11</span></span><br /><span data-ttu-id="ee8e8-128">- Soap12</span><span class="sxs-lookup"><span data-stu-id="ee8e8-128">-  Soap12</span></span><br /><br /><span data-ttu-id="ee8e8-129">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="ee8e8-130">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="ee8e8-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="ee8e8-131">writeEncoding</span></span>|<span data-ttu-id="ee8e8-132">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ee8e8-133">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="ee8e8-133">Valid values are</span></span><br /><br /> <span data-ttu-id="ee8e8-134">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="ee8e8-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="ee8e8-135">- Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="ee8e8-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="ee8e8-136">- Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="ee8e8-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="ee8e8-137">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="ee8e8-138">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee8e8-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee8e8-139">Child Elements</span></span>  
  
|<span data-ttu-id="ee8e8-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee8e8-140">Element</span></span>|<span data-ttu-id="ee8e8-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee8e8-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee8e8-142">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ee8e8-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="ee8e8-143">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ee8e8-144">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee8e8-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee8e8-145">Parent Elements</span></span>  
  
|<span data-ttu-id="ee8e8-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee8e8-146">Element</span></span>|<span data-ttu-id="ee8e8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee8e8-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee8e8-148">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ee8e8-149">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee8e8-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee8e8-150">Remarks</span></span>  
 <span data-ttu-id="ee8e8-151">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="ee8e8-152">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-152">Decoding is the reverse process.</span></span> <span data-ttu-id="ee8e8-153">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: Metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ee8e8-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ee8e8-154">`textMessageEncoding` Öğesi tarafından temsil edilen metin kodlaması en çok çalışabilen, ancak xml iletileri için en az verimli kodlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="ee8e8-155">Metin Kodlayıcısı, tel üzerinde metin tabanlı iletiler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="ee8e8-156">Bu kodlayıcı tarafından üretilen iletiler WS-\* tabanlı birlikte çalışma için uygundur.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="ee8e8-157">Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="ee8e8-158">Ancak, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamak için en düşük verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee8e8-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee8e8-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="ee8e8-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee8e8-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="ee8e8-161">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="ee8e8-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="ee8e8-162">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="ee8e8-162">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="ee8e8-163">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ee8e8-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ee8e8-164">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ee8e8-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ee8e8-165">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ee8e8-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ee8e8-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ee8e8-166">\<customBinding></span></span>](custombinding.md)
