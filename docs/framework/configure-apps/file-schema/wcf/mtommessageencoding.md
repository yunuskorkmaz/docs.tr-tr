---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 538591c85d91960eb4d4fa04caa945954ee5a997
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397709"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="b04ba-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="b04ba-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="b04ba-102">SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="b04ba-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b04ba-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b04ba-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b04ba-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b04ba-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b04ba-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b04ba-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b04ba-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b04ba-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="b04ba-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b04ba-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="b04ba-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04ba-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b04ba-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b04ba-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b04ba-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b04ba-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b04ba-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b04ba-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b04ba-112">Attributes</span></span>  
  
|<span data-ttu-id="b04ba-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b04ba-113">Attribute</span></span>|<span data-ttu-id="b04ba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b04ba-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b04ba-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="b04ba-115">maxBufferSize</span></span>|<span data-ttu-id="b04ba-116">Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b04ba-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="b04ba-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b04ba-117">maxReadPoolSize</span></span>|<span data-ttu-id="b04ba-118">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b04ba-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="b04ba-119">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b04ba-120">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-120">The default is 64.</span></span>|  
|<span data-ttu-id="b04ba-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b04ba-121">maxWritePoolSize</span></span>|<span data-ttu-id="b04ba-122">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b04ba-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="b04ba-123">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b04ba-124">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="b04ba-124">The default is 16.</span></span>|  
|<span data-ttu-id="b04ba-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="b04ba-125">messageVersion</span></span>|<span data-ttu-id="b04ba-126">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="b04ba-127">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="b04ba-127">Valid values are</span></span><br /><br /> <span data-ttu-id="b04ba-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="b04ba-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="b04ba-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="b04ba-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="b04ba-130">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="b04ba-131">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="b04ba-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="b04ba-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="b04ba-132">writeEncoding</span></span>|<span data-ttu-id="b04ba-133">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b04ba-134">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="b04ba-134">Valid values are</span></span><br /><br /> <span data-ttu-id="b04ba-135">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="b04ba-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="b04ba-136">- Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="b04ba-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="b04ba-137">- Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="b04ba-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b04ba-138">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="b04ba-139">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b04ba-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b04ba-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b04ba-140">Child Elements</span></span>  
  
|<span data-ttu-id="b04ba-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="b04ba-141">Element</span></span>|<span data-ttu-id="b04ba-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b04ba-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b04ba-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b04ba-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b04ba-144">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b04ba-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b04ba-145">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b04ba-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b04ba-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b04ba-146">Parent Elements</span></span>  
  
|<span data-ttu-id="b04ba-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="b04ba-147">Element</span></span>|<span data-ttu-id="b04ba-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b04ba-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b04ba-149">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b04ba-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b04ba-150">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b04ba-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b04ba-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b04ba-151">Remarks</span></span>  
 <span data-ttu-id="b04ba-152">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="b04ba-153">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-153">Decoding is the reverse process.</span></span> <span data-ttu-id="b04ba-154">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: Metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b04ba-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b04ba-155">`MtomMessageEncoding` Öğesi, bir ileti iletimi iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="b04ba-156">MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="b04ba-157">MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="b04ba-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="b04ba-158">MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="b04ba-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b04ba-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="b04ba-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b04ba-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b04ba-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="b04ba-161">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="b04ba-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="b04ba-162">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="b04ba-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="b04ba-163">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b04ba-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b04ba-164">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b04ba-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b04ba-165">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b04ba-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b04ba-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b04ba-166">\<customBinding></span></span>](custombinding.md)
