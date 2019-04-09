---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 7221f19dd131dbd60ef1a61625633d54dfdbe85a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191750"
---
# <a name="webmessageencoding"></a><span data-ttu-id="0a213-101">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="0a213-101">\<webMessageEncoding></span></span>
<span data-ttu-id="0a213-102">Düz metin XML'i, JavaScript nesne gösterimi (JSON) ileti Kodlamalar ve okunabilir ve bir Windows Communication Foundation (WCF) bağlaması içinde kullanıldığında yazılan için "ham" ikili içeriğin sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a213-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="0a213-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0a213-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0a213-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0a213-104">\<bindings></span></span>  
<span data-ttu-id="0a213-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0a213-105">\<customBinding></span></span>  
<span data-ttu-id="0a213-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0a213-106">\<binding></span></span>  
<span data-ttu-id="0a213-107">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="0a213-107">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a213-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a213-108">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a213-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a213-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0a213-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a213-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a213-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a213-111">Attributes</span></span>  
  
|<span data-ttu-id="0a213-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0a213-112">Attribute</span></span>|<span data-ttu-id="0a213-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a213-113">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="0a213-114">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="0a213-114">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="0a213-115">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="0a213-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="0a213-116">Her iç kodlayıcılarda (yalnızca metin, JSON ve "ham") için 64 okuyucular varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0a213-116">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="0a213-117">Bu sayı arttıkça bellek tüketimi artırılması, ancak yenilerini oluşturmak yerine, önceden oluşturulan okuyucular havuzundan kullanmanız mümkün olduğundan, gelen iletilerin ani artışları ile dağıtılacak Kodlayıcı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="0a213-117">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="0a213-118">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="0a213-118">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="0a213-119">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="0a213-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="0a213-120">Her iç kodlayıcılarda (yalnızca metin, JSON ve "ham") için 16 yazıcılar varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0a213-120">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="0a213-121">Bu sayı arttıkça bellek tüketimi artırılması, ancak yenilerini oluşturmak yerine, önceden oluşturulan yazıcılar havuzundan kullanmanız mümkün olduğundan, giden iletilerin ani artışları ile uğraşmak için Kodlayıcı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="0a213-121">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="0a213-122">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a213-122">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0a213-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0a213-123">Valid values are:</span></span><br /><br /> <span data-ttu-id="0a213-124">-   UnicodeFffeTextEncoding: Unicode büyük Endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="0a213-124">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="0a213-125">-   Utf16TextEncoding: Unicode kodlaması.</span><span class="sxs-lookup"><span data-stu-id="0a213-125">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="0a213-126">-   Utf8TextEncoding: 8-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="0a213-126">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="0a213-127">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0a213-127">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="0a213-128">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0a213-128">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a213-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a213-129">Child Elements</span></span>  
  
|<span data-ttu-id="0a213-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a213-130">Element</span></span>|<span data-ttu-id="0a213-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a213-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a213-132">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="0a213-132">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="0a213-133">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a213-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0a213-134">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0a213-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a213-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a213-135">Parent Elements</span></span>  
  
|<span data-ttu-id="0a213-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a213-136">Element</span></span>|<span data-ttu-id="0a213-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a213-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a213-138">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0a213-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0a213-139">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a213-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a213-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a213-140">Remarks</span></span>  
 <span data-ttu-id="0a213-141">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="0a213-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="0a213-142">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="0a213-142">Decoding is the reverse process.</span></span> <span data-ttu-id="0a213-143">Bu işlemler, bir karakter kodlaması belirtimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0a213-143">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="0a213-144">`webMessageEncoding` Düz metin XML ve JSON Kodlamalar ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcılar için temsilci atayarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="0a213-144">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="0a213-145">Bu temsilci bileşik ileti Kodlayıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a213-145">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="0a213-146">Bu bağlama öğesi ve kendi bileşik Kodlayıcı tarafından kullanılan SOAP ileti kullanmayan senaryolarda kodlama denetlemek için kullanılan `webHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0a213-146">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="0a213-147">Bu senaryolar, "Düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtım ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="0a213-147">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="0a213-148">Bileşik ileti Kodlayıcı SOAP veya WS-Addressing desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0a213-148">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="0a213-149">Bağlama öğesi, bir yazma karakter kullanarak kodlaması ile yapılandırılabilir `writeEncoding` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0a213-149">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="0a213-150">Sağlanan <xref:System.Text.Encoding> değeri JSON ve XML metinsel çalışmalarının yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a213-150">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="0a213-151">Okuma sırasında tüm geçerli ileti kodlama ve metin kodlaması anladım.</span><span class="sxs-lookup"><span data-stu-id="0a213-151">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 `maxReadPoolSize` <span data-ttu-id="0a213-152">ve `maxWritePoolSize` okuyucular ve yazıcılar sırasıyla ayrılacak en fazla sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a213-152">and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="0a213-153">Varsayılan olarak, 64 okuyucular ve yazıcılar 16 ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0a213-153">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="0a213-154">Varsayılan karmaşıklığı kısıtlamaları, kullanılarak da ayarlanır [ \<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) öğesi bir sınıf hizmet (DOS) reddi karşı korumak için uç nokta işlemeyi bağlamak için ileti karmaşıklığı kullanmak için bu girişim saldırıları kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="0a213-154">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a213-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a213-155">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="0a213-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a213-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="0a213-157">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="0a213-157">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="0a213-158">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="0a213-158">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="0a213-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0a213-159">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0a213-160">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="0a213-160">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0a213-161">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0a213-161">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0a213-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0a213-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
