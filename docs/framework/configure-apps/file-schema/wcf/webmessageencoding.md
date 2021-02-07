---
description: 'Hakkında daha fazla bilgi edinin: <webMessageEncoding>'
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: fb52de348ed20963a66081ac78180557f92e5e30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682572"
---
# \<webMessageEncoding>

<span data-ttu-id="2bb78-102">Düz metin XML, JavaScript Nesne Gösterimi (JSON) ileti kodlamaları ve "ham" ikili içeriğin Windows Communication Foundation (WCF) bağlamasında kullanıldığı zaman okunmalarını ve yazılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="2bb78-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="2bb78-103">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bb78-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bb78-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2bb78-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bb78-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2bb78-106">Attributes</span></span>  
  
|<span data-ttu-id="2bb78-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2bb78-107">Attribute</span></span>|<span data-ttu-id="2bb78-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bb78-108">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="2bb78-109">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="2bb78-109">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="2bb78-110">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2bb78-111">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 64 okuyucudır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-111">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="2bb78-112">Bu sayının artırılması, bellek tüketimini artırır, ancak yeni bir tane oluşturmak yerine zaten oluşturulmuş olan havuzdan okuyucuları kullanabildiğinden, Encoder 'ı gelen iletilerin ani patlayıcılarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-112">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="2bb78-113">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="2bb78-113">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="2bb78-114">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2bb78-115">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 16 yazıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-115">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="2bb78-116">Bu sayının artırılması bellek tüketimini artırır, ancak yeni olanlar oluşturmak yerine zaten oluşturulan havuzdan yazarları kullanabilmesi nedeniyle kodlayıcıyı, giden iletilerin ani burdıklarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-116">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="2bb78-117">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-117">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="2bb78-118">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="2bb78-118">Valid values are:</span></span><br /><br /> <span data-ttu-id="2bb78-119">-Unicodefffebir kodlama: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="2bb78-119">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="2bb78-120">-Utf16TextEncoding: Unicode kodlaması.</span><span class="sxs-lookup"><span data-stu-id="2bb78-120">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="2bb78-121">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="2bb78-121">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="2bb78-122">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-122">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="2bb78-123">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="2bb78-123">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bb78-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bb78-124">Child Elements</span></span>  
  
|<span data-ttu-id="2bb78-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bb78-125">Element</span></span>|<span data-ttu-id="2bb78-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bb78-126">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="2bb78-127">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-127">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2bb78-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="2bb78-128">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bb78-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bb78-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2bb78-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bb78-130">Element</span></span>|<span data-ttu-id="2bb78-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bb78-131">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="2bb78-132">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-132">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb78-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bb78-133">Remarks</span></span>  

 <span data-ttu-id="2bb78-134">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-134">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="2bb78-135">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-135">Decoding is the reverse process.</span></span> <span data-ttu-id="2bb78-136">Bu süreçler bir karakter kodlamasının belirtimini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-136">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="2bb78-137">`webMessageEncoding`Öğesi, düz metın XML ve JSON kodlamaları ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcıya temsilci seçerek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="2bb78-137">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="2bb78-138">Bu temsili bir bileşik ileti Kodlayıcısı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-138">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="2bb78-139">Bu bağlama öğesi ve onun bileşik Kodlayıcı, öğesi tarafından kullanılan SOAP mesajlaşma kullanmayan senaryolarda kodlamayı denetlemek için kullanılır `webHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="2bb78-139">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="2bb78-140">Bu senaryolar "düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtımı ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-140">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="2bb78-141">Bileşik ileti Kodlayıcısı SOAP veya WS-Addressing desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2bb78-141">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="2bb78-142">Bağlama öğesi özniteliği kullanılarak bir yazma karakteri kodlaması ile yapılandırılabilir `writeEncoding` .</span><span class="sxs-lookup"><span data-stu-id="2bb78-142">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="2bb78-143">Sağlanan <xref:System.Text.Encoding> değer, JSON ve metın XML durumları için yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-143">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="2bb78-144">Okuma sırasında, herhangi bir geçerli ileti kodlaması ve metin kodlaması anlaşılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-144">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="2bb78-145">`maxReadPoolSize``maxWritePoolSize`Ayrıca, sırasıyla ayrılacak en fazla okuyucu ve yazıcı sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bb78-145">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="2bb78-146">Varsayılan olarak 64 okuyucular ve 16 yazıcı ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-146">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="2bb78-147">Varsayılan Karmaşıklık kısıtlamaları Ayrıca, [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) uç nokta işleme kaynaklarını bağlamak üzere ileti karmaşıklığını kullanmayı deneyen bir hizmet reddi (DOS) saldırısı sınıfına karşı korumak için öğesi kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2bb78-147">Default complexity constraints are also set using the [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bb78-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="2bb78-148">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="2bb78-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb78-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="2bb78-150">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="2bb78-150">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="2bb78-151">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="2bb78-151">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2bb78-152">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2bb78-152">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2bb78-153">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2bb78-153">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2bb78-154">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2bb78-154">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
