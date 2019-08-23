---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919803"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="8154a-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="8154a-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="8154a-102">Tel Windows Communication Foundation (WCF) iletilerini kodlayan bir ikili ileti Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8154a-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="8154a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8154a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8154a-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8154a-104">\<bindings></span></span>  
<span data-ttu-id="8154a-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8154a-105">\<customBinding></span></span>  
<span data-ttu-id="8154a-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8154a-106">\<binding></span></span>  
<span data-ttu-id="8154a-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="8154a-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8154a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8154a-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8154a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8154a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8154a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8154a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8154a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8154a-111">Attributes</span></span>  
  
|<span data-ttu-id="8154a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8154a-112">Attribute</span></span>|<span data-ttu-id="8154a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8154a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8154a-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8154a-114">maxReadPoolSize</span></span>|<span data-ttu-id="8154a-115">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8154a-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="8154a-116">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8154a-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8154a-117">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8154a-117">The default is 64.</span></span>|  
|<span data-ttu-id="8154a-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="8154a-118">maxSessionSize</span></span>|<span data-ttu-id="8154a-119">Kodlama için kullanılan arabelleğin bayt cinsinden boyutunu ayarlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8154a-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="8154a-120">Daha büyük bir arabellek, çalışma kümesinin boyutunun masrafına göre kodlama hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="8154a-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="8154a-121">Varsayılan değer 2048 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8154a-121">The default is 2048.</span></span>|  
|<span data-ttu-id="8154a-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8154a-122">maxWritePoolSize</span></span>|<span data-ttu-id="8154a-123">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8154a-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="8154a-124">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8154a-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8154a-125">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="8154a-125">The default is 16.</span></span>|  
|<span data-ttu-id="8154a-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="8154a-126">messageVersion</span></span>|<span data-ttu-id="8154a-127">Kullanılan veya beklenen SOAP iletisini ve WS-Addressing sürümlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8154a-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8154a-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8154a-128">Child Elements</span></span>  
  
|<span data-ttu-id="8154a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="8154a-129">Element</span></span>|<span data-ttu-id="8154a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8154a-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8154a-131">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8154a-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="8154a-132">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8154a-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8154a-133">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8154a-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8154a-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8154a-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8154a-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="8154a-135">Element</span></span>|<span data-ttu-id="8154a-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8154a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8154a-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8154a-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="8154a-138">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8154a-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8154a-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8154a-139">Remarks</span></span>  
 <span data-ttu-id="8154a-140">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="8154a-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="8154a-141">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="8154a-141">Decoding is the reverse process.</span></span> <span data-ttu-id="8154a-142">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: Metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8154a-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="8154a-143">`binaryMessageEncoding` Öğesi, XML için .NET ikili biçimini belirtir ve karakter kodlamasını ve kullanılacak soap ve ws-Addressing sürümünü belirtme seçeneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8154a-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="8154a-144">İkili ileti Kodlayıcısı, Windows Communication Foundation (WCF) iletilerini kablo üzerinde ikili olarak kodlar.</span><span class="sxs-lookup"><span data-stu-id="8154a-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="8154a-145">Bu kodlama, iletilerin çok hızlı aktarılmasına neden olsa da, WS-\* standartlarına dayalı olarak birlikte çalışabilirlik kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="8154a-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8154a-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="8154a-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="8154a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8154a-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="8154a-148">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="8154a-148">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="8154a-149">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="8154a-149">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="8154a-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8154a-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8154a-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8154a-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8154a-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8154a-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8154a-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8154a-153">\<customBinding></span></span>](custombinding.md)
