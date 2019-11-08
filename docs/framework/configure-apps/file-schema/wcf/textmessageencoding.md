---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736210"
---
# <a name="textmessageencoding"></a><span data-ttu-id="2793a-101">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="2793a-101">\<textMessageEncoding></span></span>
<span data-ttu-id="2793a-102">Metin tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2793a-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="2793a-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2793a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2793a-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="2793a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2793a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2793a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2793a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2793a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2793a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="2793a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2793a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="2793a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2793a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2793a-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2793a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2793a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2793a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2793a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2793a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2793a-112">Attributes</span></span>  
  
|<span data-ttu-id="2793a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2793a-113">Attribute</span></span>|<span data-ttu-id="2793a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2793a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2793a-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2793a-115">maxReadPoolSize</span></span>|<span data-ttu-id="2793a-116">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2793a-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="2793a-117">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2793a-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2793a-118">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2793a-118">The default is 64.</span></span>|  
|<span data-ttu-id="2793a-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2793a-119">maxWritePoolSize</span></span>|<span data-ttu-id="2793a-120">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2793a-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="2793a-121">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2793a-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2793a-122">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="2793a-122">The default is 16.</span></span>|  
|<span data-ttu-id="2793a-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="2793a-123">messageVersion</span></span>|<span data-ttu-id="2793a-124">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2793a-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="2793a-125">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="2793a-125">Valid values are</span></span><br /><br /> <span data-ttu-id="2793a-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="2793a-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="2793a-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="2793a-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="2793a-128">- Soap11</span><span class="sxs-lookup"><span data-stu-id="2793a-128">-   Soap11</span></span><br /><span data-ttu-id="2793a-129">- Soap12</span><span class="sxs-lookup"><span data-stu-id="2793a-129">-  Soap12</span></span><br /><br /><span data-ttu-id="2793a-130">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2793a-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="2793a-131">Bu öznitelik <xref:System.ServiceModel.Channels.MessageVersion>türündedir.</span><span class="sxs-lookup"><span data-stu-id="2793a-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="2793a-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="2793a-132">writeEncoding</span></span>|<span data-ttu-id="2793a-133">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2793a-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="2793a-134">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="2793a-134">Valid values are</span></span><br /><br /> <span data-ttu-id="2793a-135">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="2793a-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="2793a-136">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="2793a-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="2793a-137">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="2793a-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="2793a-138">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="2793a-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="2793a-139">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="2793a-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2793a-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2793a-140">Child Elements</span></span>  
  
|<span data-ttu-id="2793a-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="2793a-141">Element</span></span>|<span data-ttu-id="2793a-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2793a-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2793a-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2793a-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="2793a-144">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2793a-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2793a-145">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="2793a-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2793a-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2793a-146">Parent Elements</span></span>  
  
|<span data-ttu-id="2793a-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="2793a-147">Element</span></span>|<span data-ttu-id="2793a-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2793a-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2793a-149">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="2793a-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="2793a-150">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2793a-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2793a-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2793a-151">Remarks</span></span>  
 <span data-ttu-id="2793a-152">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="2793a-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="2793a-153">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2793a-153">Decoding is the reverse process.</span></span> <span data-ttu-id="2793a-154">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="2793a-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="2793a-155">`textMessageEncoding` öğesi tarafından temsil edilen metin kodlaması en fazla birlikte çalışabilir, ancak XML iletileri için en az verimli kodlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2793a-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="2793a-156">Metin Kodlayıcısı, tel üzerinde metin tabanlı iletiler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2793a-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="2793a-157">Bu kodlayıcı tarafından üretilen iletiler WS-\* tabanlı birlikte çalışma için uygundur.</span><span class="sxs-lookup"><span data-stu-id="2793a-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="2793a-158">Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2793a-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="2793a-159">Ancak, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamak için en düşük verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="2793a-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2793a-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="2793a-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="2793a-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2793a-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="2793a-162">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="2793a-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2793a-163">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="2793a-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="2793a-164">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2793a-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2793a-165">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2793a-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2793a-166">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2793a-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2793a-167">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2793a-167">\<customBinding></span></span>](custombinding.md)
