---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738843"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="df468-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="df468-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="df468-102">SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="df468-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="df468-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="df468-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="df468-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="df468-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="df468-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="df468-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="df468-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="df468-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="df468-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="df468-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="df468-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="df468-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df468-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df468-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df468-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df468-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df468-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df468-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df468-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df468-112">Attributes</span></span>  
  
|<span data-ttu-id="df468-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df468-113">Attribute</span></span>|<span data-ttu-id="df468-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df468-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df468-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="df468-115">maxBufferSize</span></span>|<span data-ttu-id="df468-116">Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="df468-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="df468-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="df468-117">maxReadPoolSize</span></span>|<span data-ttu-id="df468-118">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="df468-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="df468-119">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="df468-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="df468-120">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="df468-120">The default is 64.</span></span>|  
|<span data-ttu-id="df468-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="df468-121">maxWritePoolSize</span></span>|<span data-ttu-id="df468-122">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="df468-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="df468-123">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="df468-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="df468-124">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="df468-124">The default is 16.</span></span>|  
|<span data-ttu-id="df468-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="df468-125">messageVersion</span></span>|<span data-ttu-id="df468-126">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="df468-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="df468-127">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="df468-127">Valid values are</span></span><br /><br /> <span data-ttu-id="df468-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="df468-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="df468-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="df468-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="df468-130">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="df468-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="df468-131">Bu öznitelik <xref:System.ServiceModel.Channels.MessageVersion>türündedir.</span><span class="sxs-lookup"><span data-stu-id="df468-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="df468-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="df468-132">writeEncoding</span></span>|<span data-ttu-id="df468-133">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="df468-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="df468-134">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="df468-134">Valid values are</span></span><br /><br /> <span data-ttu-id="df468-135">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="df468-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="df468-136">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="df468-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="df468-137">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="df468-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="df468-138">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="df468-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="df468-139">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="df468-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df468-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df468-140">Child Elements</span></span>  
  
|<span data-ttu-id="df468-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="df468-141">Element</span></span>|<span data-ttu-id="df468-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df468-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df468-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="df468-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="df468-144">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="df468-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="df468-145">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="df468-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df468-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df468-146">Parent Elements</span></span>  
  
|<span data-ttu-id="df468-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="df468-147">Element</span></span>|<span data-ttu-id="df468-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df468-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df468-149">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="df468-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="df468-150">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="df468-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df468-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df468-151">Remarks</span></span>  
 <span data-ttu-id="df468-152">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="df468-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="df468-153">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="df468-153">Decoding is the reverse process.</span></span> <span data-ttu-id="df468-154">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="df468-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="df468-155">`MtomMessageEncoding` öğesi, bir Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="df468-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="df468-156">MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="df468-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="df468-157">MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="df468-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="df468-158">MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="df468-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df468-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="df468-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="df468-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df468-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="df468-161">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="df468-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="df468-162">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="df468-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="df468-163">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="df468-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="df468-164">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="df468-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="df468-165">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="df468-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="df468-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="df468-166">\<customBinding></span></span>](custombinding.md)
