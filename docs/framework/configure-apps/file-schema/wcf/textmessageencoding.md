---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e6e6d1907d89a09a72594a836f2192e9ad9c4290
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614122"
---
# <a name="textmessageencoding"></a><span data-ttu-id="4d907-101">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="4d907-101">\<textMessageEncoding></span></span>
<span data-ttu-id="4d907-102">Karakter kodlamasını ve ileti sürüm oluşturmayı metin tabanlı XML iletileri için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d907-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="4d907-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4d907-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4d907-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4d907-104">\<bindings></span></span>  
<span data-ttu-id="4d907-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4d907-105">\<customBinding></span></span>  
<span data-ttu-id="4d907-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4d907-106">\<binding></span></span>  
<span data-ttu-id="4d907-107">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="4d907-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d907-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d907-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d907-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d907-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d907-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d907-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d907-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d907-111">Attributes</span></span>  
  
|<span data-ttu-id="4d907-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4d907-112">Attribute</span></span>|<span data-ttu-id="4d907-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d907-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d907-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4d907-114">maxReadPoolSize</span></span>|<span data-ttu-id="4d907-115">İleti sayısını belirten bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d907-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4d907-116">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="4d907-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4d907-117">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4d907-117">The default is 64.</span></span>|  
|<span data-ttu-id="4d907-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4d907-118">maxWritePoolSize</span></span>|<span data-ttu-id="4d907-119">İleti sayısını belirten bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="4d907-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4d907-120">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="4d907-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4d907-121">Varsayılan değer 16'dır.</span><span class="sxs-lookup"><span data-stu-id="4d907-121">The default is 16.</span></span>|  
|<span data-ttu-id="4d907-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="4d907-122">messageVersion</span></span>|<span data-ttu-id="4d907-123">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d907-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4d907-124">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="4d907-124">Valid values are</span></span><br /><br /> <span data-ttu-id="4d907-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="4d907-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="4d907-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4d907-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="4d907-127">-Soap11</span><span class="sxs-lookup"><span data-stu-id="4d907-127">-   Soap11</span></span><br /><span data-ttu-id="4d907-128">-Soap12</span><span class="sxs-lookup"><span data-stu-id="4d907-128">-  Soap12</span></span><br /><br /><span data-ttu-id="4d907-129">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4d907-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4d907-130">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="4d907-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4d907-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4d907-131">writeEncoding</span></span>|<span data-ttu-id="4d907-132">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d907-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4d907-133">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="4d907-133">Valid values are</span></span><br /><br /> <span data-ttu-id="4d907-134">-   UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="4d907-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4d907-135">-   Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="4d907-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4d907-136">-   Utf8TextEncoding: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="4d907-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4d907-137">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4d907-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4d907-138">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4d907-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d907-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d907-139">Child Elements</span></span>  
  
|<span data-ttu-id="4d907-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d907-140">Element</span></span>|<span data-ttu-id="4d907-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d907-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d907-142">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d907-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4d907-143">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d907-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4d907-144">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4d907-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d907-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d907-145">Parent Elements</span></span>  
  
|<span data-ttu-id="4d907-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d907-146">Element</span></span>|<span data-ttu-id="4d907-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d907-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d907-148">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4d907-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4d907-149">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d907-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d907-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d907-150">Remarks</span></span>  
 <span data-ttu-id="4d907-151">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="4d907-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4d907-152">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="4d907-152">Decoding is the reverse process.</span></span> <span data-ttu-id="4d907-153">Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4d907-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4d907-154">Metin kodlaması ile temsil edilen `textMessageEncoding` öğedir en birlikte çalışabilir, ancak XML iletileri için en az verimli Kodlayıcı.</span><span class="sxs-lookup"><span data-stu-id="4d907-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="4d907-155">Metin Kodlayıcı kablo metin tabanlı iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d907-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="4d907-156">Bu Kodlayıcı tarafından üretilen iletileri, WS - için uygun \* Interop bağlı.</span><span class="sxs-lookup"><span data-stu-id="4d907-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="4d907-157">Web hizmeti veya Web hizmeti istemcisi, metinsel XML genellikle anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d907-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4d907-158">Ancak, büyük metin olarak ikili veri blokları iletme XML iletileri kodlama az verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4d907-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d907-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d907-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4d907-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d907-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="4d907-161">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="4d907-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="4d907-162">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="4d907-162">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="4d907-163">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4d907-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4d907-164">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4d907-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4d907-165">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4d907-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4d907-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4d907-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
