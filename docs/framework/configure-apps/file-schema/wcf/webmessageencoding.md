---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: a1d776730053cd6af3c930a33e13582a8906c4d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940393"
---
# <a name="webmessageencoding"></a><span data-ttu-id="fcffc-101">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="fcffc-101">\<webMessageEncoding></span></span>
<span data-ttu-id="fcffc-102">Düz metin XML, JavaScript Nesne Gösterimi (JSON) ileti kodlamaları ve "ham" ikili içeriğin Windows Communication Foundation (WCF) bağlamasında kullanıldığı zaman okunmalarını ve yazılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcffc-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="fcffc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fcffc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="fcffc-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fcffc-104">\<bindings></span></span>  
<span data-ttu-id="fcffc-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fcffc-105">\<customBinding></span></span>  
<span data-ttu-id="fcffc-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fcffc-106">\<binding></span></span>  
<span data-ttu-id="fcffc-107">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="fcffc-107">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcffc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcffc-108">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcffc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcffc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fcffc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcffc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcffc-111">Attributes</span></span>  
  
|<span data-ttu-id="fcffc-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fcffc-112">Attribute</span></span>|<span data-ttu-id="fcffc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcffc-113">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="fcffc-114">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="fcffc-114">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="fcffc-115">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="fcffc-116">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 64 okuyucudır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-116">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="fcffc-117">Bu sayının artırılması, bellek tüketimini artırır, ancak yeni bir tane oluşturmak yerine zaten oluşturulmuş olan havuzdan okuyucuları kullanabildiğinden, Encoder 'ı gelen iletilerin ani patlayıcılarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="fcffc-117">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="fcffc-118">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="fcffc-118">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="fcffc-119">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="fcffc-120">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 16 yazıcıdır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-120">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="fcffc-121">Bu sayının artırılması bellek tüketimini artırır, ancak yeni olanlar oluşturmak yerine zaten oluşturulan havuzdan yazarları kullanabilmesi nedeniyle kodlayıcıyı, giden iletilerin ani burdıklarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="fcffc-121">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="fcffc-122">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-122">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="fcffc-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fcffc-123">Valid values are:</span></span><br /><br /> <span data-ttu-id="fcffc-124">-Unicodefffebir kodlama: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="fcffc-124">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="fcffc-125">- Utf16TextEncoding: Unicode kodlaması.</span><span class="sxs-lookup"><span data-stu-id="fcffc-125">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="fcffc-126">- Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="fcffc-126">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="fcffc-127">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-127">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="fcffc-128">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="fcffc-128">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcffc-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcffc-129">Child Elements</span></span>  
  
|<span data-ttu-id="fcffc-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcffc-130">Element</span></span>|<span data-ttu-id="fcffc-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcffc-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fcffc-132">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fcffc-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="fcffc-133">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcffc-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fcffc-134">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fcffc-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcffc-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcffc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="fcffc-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcffc-136">Element</span></span>|<span data-ttu-id="fcffc-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcffc-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcffc-138">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fcffc-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="fcffc-139">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcffc-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcffc-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcffc-140">Remarks</span></span>  
 <span data-ttu-id="fcffc-141">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="fcffc-142">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-142">Decoding is the reverse process.</span></span> <span data-ttu-id="fcffc-143">Bu süreçler bir karakter kodlamasının belirtimini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-143">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="fcffc-144">`webMessageEncoding` Öğesi, düz metin XML ve JSON kodlamaları ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcıya temsilci seçerek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="fcffc-144">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="fcffc-145">Bu temsili bir bileşik ileti Kodlayıcısı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-145">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="fcffc-146">Bu bağlama öğesi ve onun bileşik Kodlayıcı, `webHttpBinding` öğesi tarafından kullanılan soap mesajlaşma kullanmayan senaryolarda kodlamayı denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-146">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="fcffc-147">Bu senaryolar "düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtımı ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-147">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="fcffc-148">Bileşik ileti Kodlayıcısı SOAP veya WS-Addressing desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fcffc-148">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="fcffc-149">Bağlama öğesi `writeEncoding` özniteliği kullanılarak bir yazma karakteri kodlaması ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-149">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="fcffc-150">Sağlanan <xref:System.Text.Encoding> değer, JSON ve metin XML durumları için yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-150">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="fcffc-151">Okuma sırasında, herhangi bir geçerli ileti kodlaması ve metin kodlaması anlaşılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-151">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="fcffc-152">`maxReadPoolSize``maxWritePoolSize` Ayrıca, sırasıyla ayrılacak en fazla okuyucu ve yazıcı sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcffc-152">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="fcffc-153">Varsayılan olarak 64 okuyucular ve 16 yazıcı ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-153">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="fcffc-154">Varsayılan Karmaşıklık kısıtlamaları Ayrıca, uç nokta işleme kaynaklarını bağlamak üzere ileti karmaşıklığı kullanmayı deneyen bir hizmet reddi (DOS) saldırısı sınıfına karşı korumak için, [ \<ReaderQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) öğesi kullanılarak da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fcffc-154">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcffc-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcffc-155">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="fcffc-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcffc-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="fcffc-157">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="fcffc-157">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="fcffc-158">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="fcffc-158">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="fcffc-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fcffc-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fcffc-160">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="fcffc-160">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fcffc-161">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fcffc-161">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fcffc-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fcffc-162">\<customBinding></span></span>](custombinding.md)
