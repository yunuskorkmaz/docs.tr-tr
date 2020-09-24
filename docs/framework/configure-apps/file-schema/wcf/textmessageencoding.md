---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 159c581955336575af87a66a796cb78dd35d09c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158662"
---
# \<textMessageEncoding>

<span data-ttu-id="98459-101">Metin tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="98459-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="98459-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="98459-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98459-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="98459-103">Attributes and Elements</span></span>  

 <span data-ttu-id="98459-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="98459-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98459-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="98459-105">Attributes</span></span>  
  
|<span data-ttu-id="98459-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="98459-106">Attribute</span></span>|<span data-ttu-id="98459-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98459-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98459-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="98459-108">maxReadPoolSize</span></span>|<span data-ttu-id="98459-109">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="98459-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="98459-110">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="98459-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="98459-111">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="98459-111">The default is 64.</span></span>|  
|<span data-ttu-id="98459-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="98459-112">maxWritePoolSize</span></span>|<span data-ttu-id="98459-113">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="98459-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="98459-114">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="98459-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="98459-115">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="98459-115">The default is 16.</span></span>|  
|<span data-ttu-id="98459-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="98459-116">messageVersion</span></span>|<span data-ttu-id="98459-117">Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="98459-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="98459-118">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="98459-118">Valid values are</span></span><br /><br /> <span data-ttu-id="98459-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="98459-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="98459-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="98459-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="98459-121">- Soap11</span><span class="sxs-lookup"><span data-stu-id="98459-121">-   Soap11</span></span><br /><span data-ttu-id="98459-122">- Soap12</span><span class="sxs-lookup"><span data-stu-id="98459-122">-  Soap12</span></span><br /><br /><span data-ttu-id="98459-123">Varsayılan değer Soap12Addressing10 ' dir.</span><span class="sxs-lookup"><span data-stu-id="98459-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="98459-124">Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="98459-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="98459-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="98459-125">writeEncoding</span></span>|<span data-ttu-id="98459-126">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="98459-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="98459-127">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="98459-127">Valid values are</span></span><br /><br /> <span data-ttu-id="98459-128">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması</span><span class="sxs-lookup"><span data-stu-id="98459-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="98459-129">-Utf16TextEncoding: Unicode kodlaması</span><span class="sxs-lookup"><span data-stu-id="98459-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="98459-130">-Utf8TextEncoding: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="98459-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="98459-131">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="98459-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="98459-132">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="98459-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98459-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="98459-133">Child Elements</span></span>  
  
|<span data-ttu-id="98459-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="98459-134">Element</span></span>|<span data-ttu-id="98459-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98459-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="98459-136">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98459-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="98459-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="98459-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98459-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="98459-138">Parent Elements</span></span>  
  
|<span data-ttu-id="98459-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="98459-139">Element</span></span>|<span data-ttu-id="98459-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98459-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="98459-141">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98459-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98459-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98459-142">Remarks</span></span>  

 <span data-ttu-id="98459-143">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="98459-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="98459-144">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="98459-144">Decoding is the reverse process.</span></span> <span data-ttu-id="98459-145">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="98459-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="98459-146">Öğesi tarafından temsil edilen metin kodlaması `textMessageEncoding` en çok çalışabilen, ancak xml iletileri için en az verimli kodlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="98459-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="98459-147">Metin Kodlayıcısı, tel üzerinde metin tabanlı iletiler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98459-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="98459-148">Bu kodlayıcı tarafından üretilen iletiler WS-\* tabanlı birlikte çalışma için uygundur.</span><span class="sxs-lookup"><span data-stu-id="98459-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="98459-149">Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir.</span><span class="sxs-lookup"><span data-stu-id="98459-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="98459-150">Ancak, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamak için en düşük verimli yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="98459-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98459-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="98459-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="98459-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98459-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="98459-153">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="98459-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="98459-154">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="98459-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="98459-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="98459-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="98459-156">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="98459-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="98459-157">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="98459-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
