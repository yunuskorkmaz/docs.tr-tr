---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 1cdce48f51b25732c256d3c867f1bba801ec4d8c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545460"
---
# \<webMessageEncoding>
<span data-ttu-id="2b4e5-101">Düz metin XML, JavaScript Nesne Gösterimi (JSON) ileti kodlamaları ve "ham" ikili içeriğin Windows Communication Foundation (WCF) bağlamasında kullanıldığı zaman okunmalarını ve yazılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-101">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="2b4e5-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b4e5-102">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b4e5-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b4e5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2b4e5-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b4e5-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b4e5-105">Attributes</span></span>  
  
|<span data-ttu-id="2b4e5-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b4e5-106">Attribute</span></span>|<span data-ttu-id="2b4e5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b4e5-107">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="2b4e5-108">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-108">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="2b4e5-109">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-109">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2b4e5-110">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 64 okuyucudır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-110">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="2b4e5-111">Bu sayının artırılması, bellek tüketimini artırır, ancak yeni bir tane oluşturmak yerine zaten oluşturulmuş olan havuzdan okuyucuları kullanabildiğinden, Encoder 'ı gelen iletilerin ani patlayıcılarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-111">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="2b4e5-112">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-112">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="2b4e5-113">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2b4e5-114">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 16 yazıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-114">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="2b4e5-115">Bu sayının artırılması bellek tüketimini artırır, ancak yeni olanlar oluşturmak yerine zaten oluşturulan havuzdan yazarları kullanabilmesi nedeniyle kodlayıcıyı, giden iletilerin ani burdıklarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-115">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="2b4e5-116">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-116">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="2b4e5-117">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="2b4e5-117">Valid values are:</span></span><br /><br /> <span data-ttu-id="2b4e5-118">-Unicodefffebir kodlama: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-118">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="2b4e5-119">-Utf16TextEncoding: Unicode kodlaması.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-119">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="2b4e5-120">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-120">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="2b4e5-121">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-121">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="2b4e5-122">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="2b4e5-122">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b4e5-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b4e5-123">Child Elements</span></span>  
  
|<span data-ttu-id="2b4e5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b4e5-124">Element</span></span>|<span data-ttu-id="2b4e5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b4e5-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="2b4e5-126">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2b4e5-127">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="2b4e5-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b4e5-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b4e5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="2b4e5-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b4e5-129">Element</span></span>|<span data-ttu-id="2b4e5-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b4e5-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="2b4e5-131">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b4e5-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b4e5-132">Remarks</span></span>  
 <span data-ttu-id="2b4e5-133">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="2b4e5-134">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-134">Decoding is the reverse process.</span></span> <span data-ttu-id="2b4e5-135">Bu süreçler bir karakter kodlamasının belirtimini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-135">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="2b4e5-136">`webMessageEncoding`Öğesi, düz metın XML ve JSON kodlamaları ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcıya temsilci seçerek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-136">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="2b4e5-137">Bu temsili bir bileşik ileti Kodlayıcısı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-137">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="2b4e5-138">Bu bağlama öğesi ve onun bileşik Kodlayıcı, öğesi tarafından kullanılan SOAP mesajlaşma kullanmayan senaryolarda kodlamayı denetlemek için kullanılır `webHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="2b4e5-138">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="2b4e5-139">Bu senaryolar "düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtımı ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-139">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="2b4e5-140">Bileşik ileti Kodlayıcısı SOAP veya WS-Addressing desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-140">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="2b4e5-141">Bağlama öğesi özniteliği kullanılarak bir yazma karakteri kodlaması ile yapılandırılabilir `writeEncoding` .</span><span class="sxs-lookup"><span data-stu-id="2b4e5-141">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="2b4e5-142">Sağlanan <xref:System.Text.Encoding> değer, JSON ve metın XML durumları için yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-142">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="2b4e5-143">Okuma sırasında, herhangi bir geçerli ileti kodlaması ve metin kodlaması anlaşılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-143">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="2b4e5-144">`maxReadPoolSize``maxWritePoolSize`Ayrıca, sırasıyla ayrılacak en fazla okuyucu ve yazıcı sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-144">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="2b4e5-145">Varsayılan olarak 64 okuyucular ve 16 yazıcı ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-145">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="2b4e5-146">Varsayılan Karmaşıklık kısıtlamaları Ayrıca, [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) uç nokta işleme kaynaklarını bağlamak üzere ileti karmaşıklığını kullanmayı deneyen bir hizmet reddi (DOS) saldırısı sınıfına karşı korumak için öğesi kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-146">Default complexity constraints are also set using the [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b4e5-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b4e5-147">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="2b4e5-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b4e5-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="2b4e5-149">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="2b4e5-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="2b4e5-150">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="2b4e5-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2b4e5-151">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2b4e5-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2b4e5-152">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2b4e5-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2b4e5-153">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2b4e5-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
