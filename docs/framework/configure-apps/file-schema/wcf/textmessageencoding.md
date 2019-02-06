---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 6485bbd751d6467628f2191c3f5f0c6cc8a3db2f
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758657"
---
# <a name="textmessageencoding"></a><span data-ttu-id="af4f0-101">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="af4f0-101">\<textMessageEncoding></span></span>
<span data-ttu-id="af4f0-102">Karakter kodlamasını ve ileti sürüm oluşturmayı metin tabanlı XML iletileri için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="af4f0-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="af4f0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="af4f0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="af4f0-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="af4f0-104">\<bindings></span></span>  
<span data-ttu-id="af4f0-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="af4f0-105">\<customBinding></span></span>  
<span data-ttu-id="af4f0-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="af4f0-106">\<binding></span></span>  
<span data-ttu-id="af4f0-107">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="af4f0-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af4f0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af4f0-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af4f0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="af4f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="af4f0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af4f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af4f0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="af4f0-111">Attributes</span></span>  
  
|<span data-ttu-id="af4f0-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="af4f0-112">Attribute</span></span>|<span data-ttu-id="af4f0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af4f0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af4f0-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="af4f0-114">maxReadPoolSize</span></span>|<span data-ttu-id="af4f0-115">İleti sayısını belirten bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4f0-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="af4f0-116">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="af4f0-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="af4f0-117">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af4f0-117">The default is 64.</span></span>|  
|<span data-ttu-id="af4f0-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="af4f0-118">maxWritePoolSize</span></span>|<span data-ttu-id="af4f0-119">İleti sayısını belirten bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="af4f0-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="af4f0-120">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="af4f0-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="af4f0-121">Varsayılan değer 16'dır.</span><span class="sxs-lookup"><span data-stu-id="af4f0-121">The default is 16.</span></span>|  
|<span data-ttu-id="af4f0-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="af4f0-122">messageVersion</span></span>|<span data-ttu-id="af4f0-123">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="af4f0-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="af4f0-124">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="af4f0-124">Valid values are</span></span><br /><br /> <span data-ttu-id="af4f0-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="af4f0-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="af4f0-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="af4f0-126">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="af4f0-127">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af4f0-127">The default is Soap12Addressing10.</span></span> <span data-ttu-id="af4f0-128">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="af4f0-128">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="af4f0-129">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="af4f0-129">writeEncoding</span></span>|<span data-ttu-id="af4f0-130">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="af4f0-130">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="af4f0-131">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="af4f0-131">Valid values are</span></span><br /><br /> <span data-ttu-id="af4f0-132">-   UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="af4f0-132">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="af4f0-133">-   Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="af4f0-133">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="af4f0-134">-   Utf8TextEncoding: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="af4f0-134">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="af4f0-135">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="af4f0-135">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="af4f0-136">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="af4f0-136">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af4f0-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="af4f0-137">Child Elements</span></span>  
  
|<span data-ttu-id="af4f0-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="af4f0-138">Element</span></span>|<span data-ttu-id="af4f0-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af4f0-139">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af4f0-140">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="af4f0-140">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="af4f0-141">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af4f0-141">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="af4f0-142">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="af4f0-142">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af4f0-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="af4f0-143">Parent Elements</span></span>  
  
|<span data-ttu-id="af4f0-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="af4f0-144">Element</span></span>|<span data-ttu-id="af4f0-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af4f0-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af4f0-146">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="af4f0-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="af4f0-147">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af4f0-147">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af4f0-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af4f0-148">Remarks</span></span>  
 <span data-ttu-id="af4f0-149">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="af4f0-149">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="af4f0-150">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="af4f0-150">Decoding is the reverse process.</span></span> <span data-ttu-id="af4f0-151">Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="af4f0-151">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="af4f0-152">Metin kodlaması ile temsil edilen `textMessageEncoding` öğedir en birlikte çalışabilir, ancak XML iletileri için en az verimli Kodlayıcı.</span><span class="sxs-lookup"><span data-stu-id="af4f0-152">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="af4f0-153">Metin Kodlayıcı kablo metin tabanlı iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af4f0-153">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="af4f0-154">Bu Kodlayıcı tarafından üretilen iletileri, WS - için uygun \* Interop bağlı.</span><span class="sxs-lookup"><span data-stu-id="af4f0-154">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="af4f0-155">Web hizmeti veya Web hizmeti istemcisi, metinsel XML genellikle anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4f0-155">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="af4f0-156">Ancak, büyük metin olarak ikili veri blokları iletme XML iletileri kodlama az verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="af4f0-156">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af4f0-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="af4f0-157">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="af4f0-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af4f0-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="af4f0-159">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="af4f0-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="af4f0-160">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="af4f0-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="af4f0-161">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="af4f0-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="af4f0-162">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="af4f0-162">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="af4f0-163">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="af4f0-163">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="af4f0-164">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="af4f0-164">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
