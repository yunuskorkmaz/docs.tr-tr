---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: cffde19c8fd06836eaaedb5c4fc8687b97ae0afe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556186"
---
# \<mtomMessageEncoding>
<span data-ttu-id="f0064-101">SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0064-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="f0064-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0064-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0064-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0064-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f0064-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0064-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0064-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0064-105">Attributes</span></span>  
  
|<span data-ttu-id="f0064-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f0064-106">Attribute</span></span>|<span data-ttu-id="f0064-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0064-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0064-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="f0064-108">maxBufferSize</span></span>|<span data-ttu-id="f0064-109">Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f0064-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="f0064-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f0064-110">maxReadPoolSize</span></span>|<span data-ttu-id="f0064-111">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f0064-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="f0064-112">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f0064-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f0064-113">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0064-113">The default is 64.</span></span>|  
|<span data-ttu-id="f0064-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f0064-114">maxWritePoolSize</span></span>|<span data-ttu-id="f0064-115">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f0064-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="f0064-116">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f0064-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f0064-117">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="f0064-117">The default is 16.</span></span>|  
|<span data-ttu-id="f0064-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="f0064-118">messageVersion</span></span>|<span data-ttu-id="f0064-119">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0064-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="f0064-120">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="f0064-120">Valid values are</span></span><br /><br /> <span data-ttu-id="f0064-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="f0064-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="f0064-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="f0064-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="f0064-123">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0064-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="f0064-124">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="f0064-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="f0064-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="f0064-125">writeEncoding</span></span>|<span data-ttu-id="f0064-126">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0064-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f0064-127">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="f0064-127">Valid values are</span></span><br /><br /> <span data-ttu-id="f0064-128">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="f0064-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="f0064-129">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="f0064-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="f0064-130">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="f0064-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="f0064-131">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0064-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="f0064-132">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="f0064-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0064-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0064-133">Child Elements</span></span>  
  
|<span data-ttu-id="f0064-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0064-134">Element</span></span>|<span data-ttu-id="f0064-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0064-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="f0064-136">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0064-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f0064-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="f0064-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0064-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0064-138">Parent Elements</span></span>  
  
|<span data-ttu-id="f0064-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0064-139">Element</span></span>|<span data-ttu-id="f0064-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0064-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f0064-141">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0064-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0064-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0064-142">Remarks</span></span>  
 <span data-ttu-id="f0064-143">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f0064-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="f0064-144">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f0064-144">Decoding is the reverse process.</span></span> <span data-ttu-id="f0064-145">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f0064-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="f0064-146">`MtomMessageEncoding`Öğesi, bir Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0064-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="f0064-147">MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="f0064-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="f0064-148">MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f0064-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="f0064-149">MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="f0064-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0064-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0064-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f0064-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0064-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="f0064-152">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="f0064-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="f0064-153">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="f0064-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="f0064-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0064-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f0064-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f0064-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f0064-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0064-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
