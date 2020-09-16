---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 4179d7ac1919610b0be131b079b28da0cd9cad75
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540301"
---
# \<binaryMessageEncoding>
<span data-ttu-id="376a6-101">Tel Windows Communication Foundation (WCF) iletilerini kodlayan bir ikili ileti Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="376a6-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="376a6-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="376a6-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="376a6-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="376a6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="376a6-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="376a6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="376a6-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="376a6-105">Attributes</span></span>  
  
|<span data-ttu-id="376a6-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="376a6-106">Attribute</span></span>|<span data-ttu-id="376a6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="376a6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="376a6-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="376a6-108">maxReadPoolSize</span></span>|<span data-ttu-id="376a6-109">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="376a6-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="376a6-110">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="376a6-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="376a6-111">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="376a6-111">The default is 64.</span></span>|  
|<span data-ttu-id="376a6-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="376a6-112">maxSessionSize</span></span>|<span data-ttu-id="376a6-113">Kodlama için kullanılan arabelleğin bayt cinsinden boyutunu ayarlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="376a6-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="376a6-114">Daha büyük bir arabellek, çalışma kümesinin boyutunun masrafına göre kodlama hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="376a6-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="376a6-115">Varsayılan değer 2048 ' dir.</span><span class="sxs-lookup"><span data-stu-id="376a6-115">The default is 2048.</span></span>|  
|<span data-ttu-id="376a6-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="376a6-116">maxWritePoolSize</span></span>|<span data-ttu-id="376a6-117">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="376a6-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="376a6-118">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="376a6-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="376a6-119">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="376a6-119">The default is 16.</span></span>|  
|<span data-ttu-id="376a6-120">messageVersion</span><span class="sxs-lookup"><span data-stu-id="376a6-120">messageVersion</span></span>|<span data-ttu-id="376a6-121">Kullanılan veya beklenen SOAP iletisini ve WS-Addressing sürümlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="376a6-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="376a6-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="376a6-122">Child Elements</span></span>  
  
|<span data-ttu-id="376a6-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="376a6-123">Element</span></span>|<span data-ttu-id="376a6-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="376a6-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="376a6-125">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="376a6-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="376a6-126">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="376a6-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="376a6-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="376a6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="376a6-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="376a6-128">Element</span></span>|<span data-ttu-id="376a6-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="376a6-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="376a6-130">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="376a6-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="376a6-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="376a6-131">Remarks</span></span>  
 <span data-ttu-id="376a6-132">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="376a6-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="376a6-133">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="376a6-133">Decoding is the reverse process.</span></span> <span data-ttu-id="376a6-134">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="376a6-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="376a6-135">`binaryMessageEncoding`Öğesi, XML için .net Ikili biçimini belirtir ve karakter kodlamasını ve kullanılacak soap ve ws-Addressing sürümünü belirtme seçeneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="376a6-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="376a6-136">İkili ileti Kodlayıcısı, Windows Communication Foundation (WCF) iletilerini kablo üzerinde ikili olarak kodlar.</span><span class="sxs-lookup"><span data-stu-id="376a6-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="376a6-137">Bu kodlama, iletilerin çok hızlı aktarılmasına neden olsa da, WS-\* standartlarına dayalı olarak birlikte çalışabilirlik kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="376a6-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="376a6-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="376a6-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="376a6-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="376a6-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="376a6-140">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="376a6-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="376a6-141">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="376a6-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="376a6-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="376a6-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="376a6-143">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="376a6-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="376a6-144">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="376a6-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
