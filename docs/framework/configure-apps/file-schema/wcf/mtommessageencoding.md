---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738843"
---
# \<mtomMessageEncoding>
<span data-ttu-id="a7f0c-101">SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="a7f0c-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7f0c-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f0c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f0c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f0c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f0c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7f0c-105">Attributes</span></span>  
  
|<span data-ttu-id="a7f0c-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7f0c-106">Attribute</span></span>|<span data-ttu-id="a7f0c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f0c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7f0c-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a7f0c-108">maxBufferSize</span></span>|<span data-ttu-id="a7f0c-109">Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="a7f0c-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a7f0c-110">maxReadPoolSize</span></span>|<span data-ttu-id="a7f0c-111">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a7f0c-112">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a7f0c-113">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-113">The default is 64.</span></span>|  
|<span data-ttu-id="a7f0c-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a7f0c-114">maxWritePoolSize</span></span>|<span data-ttu-id="a7f0c-115">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a7f0c-116">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a7f0c-117">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-117">The default is 16.</span></span>|  
|<span data-ttu-id="a7f0c-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a7f0c-118">messageVersion</span></span>|<span data-ttu-id="a7f0c-119">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="a7f0c-120">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="a7f0c-120">Valid values are</span></span><br /><br /> <span data-ttu-id="a7f0c-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="a7f0c-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="a7f0c-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="a7f0c-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="a7f0c-123">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="a7f0c-124">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="a7f0c-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="a7f0c-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="a7f0c-125">writeEncoding</span></span>|<span data-ttu-id="a7f0c-126">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a7f0c-127">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="a7f0c-127">Valid values are</span></span><br /><br /> <span data-ttu-id="a7f0c-128">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="a7f0c-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="a7f0c-129">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="a7f0c-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="a7f0c-130">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="a7f0c-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a7f0c-131">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="a7f0c-132">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="a7f0c-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f0c-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f0c-133">Child Elements</span></span>  
  
|<span data-ttu-id="a7f0c-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7f0c-134">Element</span></span>|<span data-ttu-id="a7f0c-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f0c-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="a7f0c-136">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a7f0c-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="a7f0c-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f0c-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f0c-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f0c-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7f0c-139">Element</span></span>|<span data-ttu-id="a7f0c-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f0c-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a7f0c-141">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f0c-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7f0c-142">Remarks</span></span>  
 <span data-ttu-id="a7f0c-143">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a7f0c-144">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-144">Decoding is the reverse process.</span></span> <span data-ttu-id="a7f0c-145">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a7f0c-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a7f0c-146">`MtomMessageEncoding`Öğesi, bir Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="a7f0c-147">MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="a7f0c-148">MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="a7f0c-149">MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f0c-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7f0c-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a7f0c-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f0c-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="a7f0c-152">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="a7f0c-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="a7f0c-153">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="a7f0c-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="a7f0c-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a7f0c-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7f0c-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a7f0c-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a7f0c-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a7f0c-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
