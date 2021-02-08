---
description: 'Hakkında daha fazla bilgi edinin: <textMessageEncoding>'
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: a8c7820b2e22152850d6d21c5091e328feb7a9f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786609"
---
# \<textMessageEncoding>

<span data-ttu-id="9f9d5-102">Metin tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="9f9d5-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f9d5-103">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f9d5-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f9d5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9f9d5-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f9d5-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f9d5-106">Attributes</span></span>  
  
|<span data-ttu-id="9f9d5-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f9d5-107">Attribute</span></span>|<span data-ttu-id="9f9d5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f9d5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f9d5-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="9f9d5-109">maxReadPoolSize</span></span>|<span data-ttu-id="9f9d5-110">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-110">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="9f9d5-111">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-111">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9f9d5-112">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-112">The default is 64.</span></span>|  
|<span data-ttu-id="9f9d5-113">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="9f9d5-113">maxWritePoolSize</span></span>|<span data-ttu-id="9f9d5-114">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-114">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="9f9d5-115">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9f9d5-116">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-116">The default is 16.</span></span>|  
|<span data-ttu-id="9f9d5-117">messageVersion</span><span class="sxs-lookup"><span data-stu-id="9f9d5-117">messageVersion</span></span>|<span data-ttu-id="9f9d5-118">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-118">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="9f9d5-119">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="9f9d5-119">Valid values are</span></span><br /><br /> <span data-ttu-id="9f9d5-120">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="9f9d5-120">-   Soap11Addressing10</span></span><br /><span data-ttu-id="9f9d5-121">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="9f9d5-121">-   Soap12Addressing10</span></span><br /><span data-ttu-id="9f9d5-122">- Soap11</span><span class="sxs-lookup"><span data-stu-id="9f9d5-122">-   Soap11</span></span><br /><span data-ttu-id="9f9d5-123">- Soap12</span><span class="sxs-lookup"><span data-stu-id="9f9d5-123">-  Soap12</span></span><br /><br /><span data-ttu-id="9f9d5-124">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-124">The default is Soap12Addressing10.</span></span> <span data-ttu-id="9f9d5-125">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="9f9d5-125">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="9f9d5-126">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="9f9d5-126">writeEncoding</span></span>|<span data-ttu-id="9f9d5-127">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-127">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9f9d5-128">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="9f9d5-128">Valid values are</span></span><br /><br /> <span data-ttu-id="9f9d5-129">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="9f9d5-129">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="9f9d5-130">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="9f9d5-130">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="9f9d5-131">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="9f9d5-131">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9f9d5-132">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-132">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="9f9d5-133">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="9f9d5-133">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f9d5-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f9d5-134">Child Elements</span></span>  
  
|<span data-ttu-id="9f9d5-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f9d5-135">Element</span></span>|<span data-ttu-id="9f9d5-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f9d5-136">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9f9d5-137">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-137">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9f9d5-138">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="9f9d5-138">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f9d5-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f9d5-139">Parent Elements</span></span>  
  
|<span data-ttu-id="9f9d5-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f9d5-140">Element</span></span>|<span data-ttu-id="9f9d5-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f9d5-141">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="9f9d5-142">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-142">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9d5-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f9d5-143">Remarks</span></span>  

 <span data-ttu-id="9f9d5-144">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-144">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="9f9d5-145">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-145">Decoding is the reverse process.</span></span> <span data-ttu-id="9f9d5-146">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="9f9d5-146">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="9f9d5-147">Öğesi tarafından temsil edilen metin kodlaması `textMessageEncoding` en çok çalışabilen, ancak xml iletileri için en az verimli kodlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-147">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="9f9d5-148">Metin Kodlayıcısı, tel üzerinde metin tabanlı iletiler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-148">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="9f9d5-149">Bu kodlayıcı tarafından üretilen iletiler WS-\* tabanlı birlikte çalışma için uygundur.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-149">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="9f9d5-150">Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-150">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="9f9d5-151">Ancak, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamak için en düşük verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-151">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9d5-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f9d5-152">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9f9d5-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f9d5-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="9f9d5-154">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="9f9d5-154">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="9f9d5-155">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="9f9d5-155">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="9f9d5-156">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9f9d5-156">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f9d5-157">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9f9d5-157">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9f9d5-158">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9f9d5-158">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
