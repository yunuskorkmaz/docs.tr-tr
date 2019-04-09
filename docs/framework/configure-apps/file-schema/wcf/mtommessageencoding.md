---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 61b23957c56bad81598dd65b0dd68f7b44d329e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146802"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="28242-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="28242-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="28242-102">SOAP ileti aktarım en iyi duruma getirme mekanizması (temel MTOM) iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="28242-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="28242-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="28242-103">\<system.serviceModel></span></span>  
<span data-ttu-id="28242-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="28242-104">\<bindings></span></span>  
<span data-ttu-id="28242-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="28242-105">\<customBinding></span></span>  
<span data-ttu-id="28242-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="28242-106">\<binding></span></span>  
<span data-ttu-id="28242-107">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="28242-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28242-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28242-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28242-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="28242-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28242-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28242-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28242-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28242-111">Attributes</span></span>  
  
|<span data-ttu-id="28242-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="28242-112">Attribute</span></span>|<span data-ttu-id="28242-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28242-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28242-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="28242-114">maxBufferSize</span></span>|<span data-ttu-id="28242-115">Kullanılabilir arabelleğinin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="28242-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="28242-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="28242-116">maxReadPoolSize</span></span>|<span data-ttu-id="28242-117">İleti sayısını belirten bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28242-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="28242-118">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="28242-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="28242-119">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="28242-119">The default is 64.</span></span>|  
|<span data-ttu-id="28242-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="28242-120">maxWritePoolSize</span></span>|<span data-ttu-id="28242-121">İleti sayısını belirten bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="28242-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="28242-122">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="28242-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="28242-123">Varsayılan değer 16'dır.</span><span class="sxs-lookup"><span data-stu-id="28242-123">The default is 16.</span></span>|  
|<span data-ttu-id="28242-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="28242-124">messageVersion</span></span>|<span data-ttu-id="28242-125">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="28242-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="28242-126">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="28242-126">Valid values are</span></span><br /><br /> <span data-ttu-id="28242-127">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="28242-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="28242-128">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="28242-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="28242-129">Soap12Addressing10 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="28242-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="28242-130">Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="28242-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="28242-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="28242-131">writeEncoding</span></span>|<span data-ttu-id="28242-132">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="28242-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="28242-133">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="28242-133">Valid values are</span></span><br /><br /> <span data-ttu-id="28242-134">-   UnicodeFffeTextEncoding: Unicode kodlama BigEndian</span><span class="sxs-lookup"><span data-stu-id="28242-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="28242-135">-   Utf16TextEncoding: Unicode kodlama</span><span class="sxs-lookup"><span data-stu-id="28242-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="28242-136">-   Utf8TextEncoding: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="28242-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="28242-137">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="28242-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="28242-138">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="28242-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28242-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="28242-139">Child Elements</span></span>  
  
|<span data-ttu-id="28242-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="28242-140">Element</span></span>|<span data-ttu-id="28242-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28242-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28242-142">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="28242-142">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="28242-143">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28242-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="28242-144">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="28242-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28242-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="28242-145">Parent Elements</span></span>  
  
|<span data-ttu-id="28242-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="28242-146">Element</span></span>|<span data-ttu-id="28242-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28242-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28242-148">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="28242-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="28242-149">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28242-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28242-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28242-150">Remarks</span></span>  
 <span data-ttu-id="28242-151">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="28242-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="28242-152">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="28242-152">Decoding is the reverse process.</span></span> <span data-ttu-id="28242-153">Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="28242-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="28242-154">`MtomMessageEncoding` Öğesi, karakter kodlamasını ve ileti sürüm oluşturmayı ve bir ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlaması kullanarak iletiler için kullanılan diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="28242-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="28242-155">MTOM WCF iletilerinde ikili veri aktarımı için verimli bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="28242-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="28242-156">MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="28242-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="28242-157">MTOM kodlama çoğu XML metin biçiminde aktarır, ancak büyük ikili veri blokları olarak ileterek iyileştirir-base64 kodlu biçimlerini dönüştürme olmadan olduğu.</span><span class="sxs-lookup"><span data-stu-id="28242-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28242-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="28242-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="28242-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28242-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="28242-160">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="28242-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="28242-161">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="28242-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="28242-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="28242-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="28242-163">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="28242-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="28242-164">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="28242-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="28242-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="28242-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
