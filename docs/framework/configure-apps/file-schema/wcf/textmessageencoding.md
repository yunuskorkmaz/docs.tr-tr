---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 0ee50a4b5adeede2dd531ba734ac9fb420f3b713
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150246"
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="9020f-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="9020f-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="9020f-103">Karakter kodlamasını ve ileti sürüm oluşturmayı metin tabanlı XML iletileri için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="9020f-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="9020f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9020f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9020f-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9020f-105">\<bindings></span></span>  
<span data-ttu-id="9020f-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9020f-106">\<customBinding></span></span>  
<span data-ttu-id="9020f-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9020f-107">\<binding></span></span>  
<span data-ttu-id="9020f-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="9020f-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9020f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9020f-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9020f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9020f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9020f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9020f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9020f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9020f-112">Attributes</span></span>  
  
|<span data-ttu-id="9020f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9020f-113">Attribute</span></span>|<span data-ttu-id="9020f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9020f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9020f-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="9020f-115">maxReadPoolSize</span></span>|<span data-ttu-id="9020f-116">İleti sayısını belirten bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9020f-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="9020f-117">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="9020f-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9020f-118">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9020f-118">The default is 64.</span></span>|  
|<span data-ttu-id="9020f-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="9020f-119">maxWritePoolSize</span></span>|<span data-ttu-id="9020f-120">İleti sayısını belirten bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="9020f-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="9020f-121">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="9020f-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9020f-122">Varsayılan değer 16'dır.</span><span class="sxs-lookup"><span data-stu-id="9020f-122">The default is 16.</span></span>|  
|<span data-ttu-id="9020f-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="9020f-123">messageVersion</span></span>|<span data-ttu-id="9020f-124">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9020f-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="9020f-125">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="9020f-125">Valid values are</span></span><br /><br /> <span data-ttu-id="9020f-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="9020f-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="9020f-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="9020f-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="9020f-128">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9020f-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="9020f-129">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="9020f-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="9020f-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="9020f-130">writeEncoding</span></span>|<span data-ttu-id="9020f-131">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9020f-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9020f-132">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="9020f-132">Valid values are</span></span><br /><br /> <span data-ttu-id="9020f-133">-UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="9020f-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="9020f-134">-Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="9020f-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="9020f-135">-Utf8TextEncoding: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="9020f-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9020f-136">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9020f-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="9020f-137">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="9020f-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9020f-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9020f-138">Child Elements</span></span>  
  
|<span data-ttu-id="9020f-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="9020f-139">Element</span></span>|<span data-ttu-id="9020f-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9020f-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9020f-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="9020f-141">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="9020f-142">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9020f-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9020f-143">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9020f-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9020f-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9020f-144">Parent Elements</span></span>  
  
|<span data-ttu-id="9020f-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="9020f-145">Element</span></span>|<span data-ttu-id="9020f-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9020f-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9020f-147">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9020f-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9020f-148">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9020f-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9020f-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9020f-149">Remarks</span></span>  
 <span data-ttu-id="9020f-150">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9020f-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="9020f-151">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9020f-151">Decoding is the reverse process.</span></span> <span data-ttu-id="9020f-152">Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="9020f-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="9020f-153">Metin kodlaması ile temsil edilen `textMessageEncoding` öğedir en birlikte çalışabilir, ancak XML iletileri için en az verimli Kodlayıcı.</span><span class="sxs-lookup"><span data-stu-id="9020f-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="9020f-154">Metin Kodlayıcı kablo metin tabanlı iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9020f-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="9020f-155">Bu Kodlayıcı tarafından üretilen iletileri, WS - için uygun \* Interop bağlı.</span><span class="sxs-lookup"><span data-stu-id="9020f-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="9020f-156">Web hizmeti veya Web hizmeti istemcisi, metinsel XML genellikle anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9020f-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="9020f-157">Ancak, büyük metin olarak ikili veri blokları iletme XML iletileri kodlama az verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9020f-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9020f-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="9020f-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9020f-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9020f-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="9020f-160">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="9020f-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="9020f-161">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="9020f-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="9020f-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9020f-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9020f-163">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9020f-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9020f-164">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9020f-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9020f-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9020f-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
