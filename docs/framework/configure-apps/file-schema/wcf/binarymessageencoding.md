---
title: '&lt;binaryMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 7753340be01c407157d9a0576f31db4245c0b4f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672857"
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="84a68-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="84a68-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="84a68-103">Kablodaki ikili Windows Communication Foundation (WCF) iletilerini kodlayan bir ikili ileti Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84a68-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="84a68-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="84a68-104">\<system.serviceModel></span></span>  
<span data-ttu-id="84a68-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="84a68-105">\<bindings></span></span>  
<span data-ttu-id="84a68-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="84a68-106">\<customBinding></span></span>  
<span data-ttu-id="84a68-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="84a68-107">\<binding></span></span>  
<span data-ttu-id="84a68-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="84a68-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84a68-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84a68-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84a68-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="84a68-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84a68-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84a68-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84a68-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="84a68-112">Attributes</span></span>  
  
|<span data-ttu-id="84a68-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="84a68-113">Attribute</span></span>|<span data-ttu-id="84a68-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84a68-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84a68-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="84a68-115">maxReadPoolSize</span></span>|<span data-ttu-id="84a68-116">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84a68-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="84a68-117">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="84a68-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="84a68-118">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="84a68-118">The default is 64.</span></span>|  
|<span data-ttu-id="84a68-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="84a68-119">maxSessionSize</span></span>|<span data-ttu-id="84a68-120">Bir pozitif tamsayı kodlamak için kullanılan arabelleğin bayt cinsinden boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="84a68-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="84a68-121">Daha büyük bir arabellek çalışma kümesi boyutu çoğaltamaz kodlama hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="84a68-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="84a68-122">2048 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="84a68-122">The default is 2048.</span></span>|  
|<span data-ttu-id="84a68-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="84a68-123">maxWritePoolSize</span></span>|<span data-ttu-id="84a68-124">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="84a68-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="84a68-125">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="84a68-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="84a68-126">Varsayılan değer 16'dır.</span><span class="sxs-lookup"><span data-stu-id="84a68-126">The default is 16.</span></span>|  
|<span data-ttu-id="84a68-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="84a68-127">messageVersion</span></span>|<span data-ttu-id="84a68-128">SOAP iletisi ve kullanılan veya beklenen WS-Addressing sürümleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="84a68-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84a68-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="84a68-129">Child Elements</span></span>  
  
|<span data-ttu-id="84a68-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="84a68-130">Element</span></span>|<span data-ttu-id="84a68-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84a68-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84a68-132">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="84a68-132">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="84a68-133">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84a68-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="84a68-134">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="84a68-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84a68-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="84a68-135">Parent Elements</span></span>  
  
|<span data-ttu-id="84a68-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="84a68-136">Element</span></span>|<span data-ttu-id="84a68-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84a68-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84a68-138">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="84a68-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="84a68-139">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84a68-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a68-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84a68-140">Remarks</span></span>  
 <span data-ttu-id="84a68-141">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="84a68-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="84a68-142">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="84a68-142">Decoding is the reverse process.</span></span> <span data-ttu-id="84a68-143">Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="84a68-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="84a68-144">`binaryMessageEncoding` Öğesi için XML .NET ikili biçimini belirtir ve karakter kodlamasını belirtmek için seçenekleri ve kullanılmak üzere SOAP ve WS-Addressing sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="84a68-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="84a68-145">İkili ileti Kodlayıcısı Kablodaki ikili Windows Communication Foundation (WCF) iletilerini kodlayan.</span><span class="sxs-lookup"><span data-stu-id="84a68-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="84a68-146">Bu kodlama ileti çok hızlı aktarımını sonuçları karşın, birlikte çalışabilirlik tabanlı WS - üzerinde \* standartları kaybolur.</span><span class="sxs-lookup"><span data-stu-id="84a68-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a68-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="84a68-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="84a68-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84a68-148">See also</span></span>
- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="84a68-149">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="84a68-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="84a68-150">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="84a68-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="84a68-151">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="84a68-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="84a68-152">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="84a68-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="84a68-153">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="84a68-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="84a68-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="84a68-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
