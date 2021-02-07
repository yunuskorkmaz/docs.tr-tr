---
description: 'Hakkında daha fazla bilgi edinin: <mtomMessageEncoding>'
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 37ac0be5f3de84a4c310b8ec2a09ed6f3c4def56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684119"
---
# \<mtomMessageEncoding>

<span data-ttu-id="96beb-102">SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="96beb-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="96beb-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="96beb-103">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96beb-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="96beb-104">Attributes and Elements</span></span>  

 <span data-ttu-id="96beb-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96beb-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96beb-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="96beb-106">Attributes</span></span>  
  
|<span data-ttu-id="96beb-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="96beb-107">Attribute</span></span>|<span data-ttu-id="96beb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96beb-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96beb-109">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="96beb-109">maxBufferSize</span></span>|<span data-ttu-id="96beb-110">Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="96beb-110">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="96beb-111">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="96beb-111">maxReadPoolSize</span></span>|<span data-ttu-id="96beb-112">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="96beb-112">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="96beb-113">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="96beb-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="96beb-114">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="96beb-114">The default is 64.</span></span>|  
|<span data-ttu-id="96beb-115">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="96beb-115">maxWritePoolSize</span></span>|<span data-ttu-id="96beb-116">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="96beb-116">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="96beb-117">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="96beb-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="96beb-118">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="96beb-118">The default is 16.</span></span>|  
|<span data-ttu-id="96beb-119">messageVersion</span><span class="sxs-lookup"><span data-stu-id="96beb-119">messageVersion</span></span>|<span data-ttu-id="96beb-120">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="96beb-120">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="96beb-121">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="96beb-121">Valid values are</span></span><br /><br /> <span data-ttu-id="96beb-122">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="96beb-122">-   Soap11Addressing1</span></span><br /><span data-ttu-id="96beb-123">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="96beb-123">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="96beb-124">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="96beb-124">The default is Soap12Addressing10.</span></span> <span data-ttu-id="96beb-125">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="96beb-125">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="96beb-126">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="96beb-126">writeEncoding</span></span>|<span data-ttu-id="96beb-127">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96beb-127">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="96beb-128">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="96beb-128">Valid values are</span></span><br /><br /> <span data-ttu-id="96beb-129">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="96beb-129">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="96beb-130">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="96beb-130">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="96beb-131">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="96beb-131">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="96beb-132">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="96beb-132">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="96beb-133">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="96beb-133">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96beb-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="96beb-134">Child Elements</span></span>  
  
|<span data-ttu-id="96beb-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="96beb-135">Element</span></span>|<span data-ttu-id="96beb-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96beb-136">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="96beb-137">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="96beb-137">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="96beb-138">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="96beb-138">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96beb-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="96beb-139">Parent Elements</span></span>  
  
|<span data-ttu-id="96beb-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="96beb-140">Element</span></span>|<span data-ttu-id="96beb-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96beb-141">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="96beb-142">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="96beb-142">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96beb-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96beb-143">Remarks</span></span>  

 <span data-ttu-id="96beb-144">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="96beb-144">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="96beb-145">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="96beb-145">Decoding is the reverse process.</span></span> <span data-ttu-id="96beb-146">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="96beb-146">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="96beb-147">`MtomMessageEncoding`Öğesi, bir Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="96beb-147">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="96beb-148">MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="96beb-148">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="96beb-149">MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="96beb-149">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="96beb-150">MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="96beb-150">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96beb-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="96beb-151">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="96beb-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96beb-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="96beb-153">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="96beb-153">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="96beb-154">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="96beb-154">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="96beb-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="96beb-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="96beb-156">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="96beb-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="96beb-157">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="96beb-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
