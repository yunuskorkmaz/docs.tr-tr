---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: e02ed6ef79fcf52bbe9c33bd9b36a14113e19d1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228386"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="74dd5-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="74dd5-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="74dd5-102">Kablodaki ikili Windows Communication Foundation (WCF) iletilerini kodlayan bir ikili ileti Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74dd5-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="74dd5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74dd5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="74dd5-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="74dd5-104">\<bindings></span></span>  
<span data-ttu-id="74dd5-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="74dd5-105">\<customBinding></span></span>  
<span data-ttu-id="74dd5-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="74dd5-106">\<binding></span></span>  
<span data-ttu-id="74dd5-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="74dd5-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74dd5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74dd5-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74dd5-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74dd5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="74dd5-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74dd5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74dd5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74dd5-111">Attributes</span></span>  
  
|<span data-ttu-id="74dd5-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="74dd5-112">Attribute</span></span>|<span data-ttu-id="74dd5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74dd5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74dd5-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="74dd5-114">maxReadPoolSize</span></span>|<span data-ttu-id="74dd5-115">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74dd5-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="74dd5-116">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="74dd5-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="74dd5-117">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="74dd5-117">The default is 64.</span></span>|  
|<span data-ttu-id="74dd5-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="74dd5-118">maxSessionSize</span></span>|<span data-ttu-id="74dd5-119">Bir pozitif tamsayı kodlamak için kullanılan arabelleğin bayt cinsinden boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="74dd5-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="74dd5-120">Daha büyük bir arabellek çalışma kümesi boyutu çoğaltamaz kodlama hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="74dd5-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="74dd5-121">2048 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="74dd5-121">The default is 2048.</span></span>|  
|<span data-ttu-id="74dd5-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="74dd5-122">maxWritePoolSize</span></span>|<span data-ttu-id="74dd5-123">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="74dd5-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="74dd5-124">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="74dd5-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="74dd5-125">Varsayılan değer 16'dır.</span><span class="sxs-lookup"><span data-stu-id="74dd5-125">The default is 16.</span></span>|  
|<span data-ttu-id="74dd5-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="74dd5-126">messageVersion</span></span>|<span data-ttu-id="74dd5-127">SOAP iletisi ve kullanılan veya beklenen WS-Addressing sürümleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="74dd5-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74dd5-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74dd5-128">Child Elements</span></span>  
  
|<span data-ttu-id="74dd5-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="74dd5-129">Element</span></span>|<span data-ttu-id="74dd5-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74dd5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74dd5-131">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="74dd5-131">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="74dd5-132">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74dd5-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="74dd5-133">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="74dd5-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74dd5-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74dd5-134">Parent Elements</span></span>  
  
|<span data-ttu-id="74dd5-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="74dd5-135">Element</span></span>|<span data-ttu-id="74dd5-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74dd5-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74dd5-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="74dd5-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="74dd5-138">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74dd5-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74dd5-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74dd5-139">Remarks</span></span>  
 <span data-ttu-id="74dd5-140">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="74dd5-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="74dd5-141">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="74dd5-141">Decoding is the reverse process.</span></span> <span data-ttu-id="74dd5-142">Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="74dd5-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="74dd5-143">`binaryMessageEncoding` Öğesi için XML .NET ikili biçimini belirtir ve karakter kodlamasını belirtmek için seçenekleri ve kullanılmak üzere SOAP ve WS-Addressing sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="74dd5-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="74dd5-144">İkili ileti Kodlayıcısı Kablodaki ikili Windows Communication Foundation (WCF) iletilerini kodlayan.</span><span class="sxs-lookup"><span data-stu-id="74dd5-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="74dd5-145">Bu kodlama ileti çok hızlı aktarımını sonuçları karşın, birlikte çalışabilirlik tabanlı WS - üzerinde \* standartları kaybolur.</span><span class="sxs-lookup"><span data-stu-id="74dd5-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74dd5-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="74dd5-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="74dd5-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74dd5-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="74dd5-148">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="74dd5-148">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="74dd5-149">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="74dd5-149">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="74dd5-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="74dd5-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="74dd5-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="74dd5-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="74dd5-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="74dd5-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="74dd5-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="74dd5-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
