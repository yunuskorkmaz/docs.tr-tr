---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: fc1f83128dacb588d8179dea95c132da1ab2be91
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755272"
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="cb651-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="cb651-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="cb651-103">Düz metin XML, JavaScript nesne gösterimi (JSON) ileti Kodlamalar ve okunabilir ve yazılabilir bir Windows Communication Foundation (WCF) bağlama kullanıldığında için "ham" ikili içerik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb651-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="cb651-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cb651-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cb651-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cb651-105">\<bindings></span></span>  
<span data-ttu-id="cb651-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb651-106">\<customBinding></span></span>  
<span data-ttu-id="cb651-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb651-107">\<binding></span></span>  
<span data-ttu-id="cb651-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="cb651-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb651-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb651-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb651-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb651-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cb651-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb651-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb651-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb651-112">Attributes</span></span>  
  
|<span data-ttu-id="cb651-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb651-113">Attribute</span></span>|<span data-ttu-id="cb651-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb651-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="cb651-115">Yeni okuyucu ayırmadan aynı anda okunabilir iletilerin miktarı.</span><span class="sxs-lookup"><span data-stu-id="cb651-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="cb651-116">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="cb651-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cb651-117">64 okuyucular her iç kodlayıcılar (yalnızca metin, JSON ve "ham") için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb651-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="cb651-118">Bu sayı artar bellek tüketimi artırılması, ancak yeni kampanya oluşturmak yerine zaten oluşturulmuştur havuz okuyuculardan kullanmanız mümkün olduğundan gelen iletileri ani WINS'e ile mücadele etmek için Kodlayıcı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="cb651-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="cb651-119">Yeni yazıcı ayırmadan aynı anda gönderilebilir iletilerin miktarı.</span><span class="sxs-lookup"><span data-stu-id="cb651-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="cb651-120">Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun.</span><span class="sxs-lookup"><span data-stu-id="cb651-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cb651-121">Her iç kodlayıcılar (yalnızca metin, JSON ve "ham") için 16 yazıcılarının varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb651-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="cb651-122">Bu sayı artar bellek tüketimi artırılması, ancak yeni kampanya oluşturmak yerine, önceden oluşturulan yazıcılarının havuzundan kullanmanız mümkün olduğundan Giden iletiler ani WINS'e ile mücadele etmek için Kodlayıcı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="cb651-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="cb651-123">Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb651-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="cb651-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cb651-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="cb651-125">-UnicodeFffeTextEncoding: Unicode Big Endian'ya kodlaması.</span><span class="sxs-lookup"><span data-stu-id="cb651-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="cb651-126">-Utf16TextEncoding: Unicode kodlama.</span><span class="sxs-lookup"><span data-stu-id="cb651-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="cb651-127">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="cb651-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="cb651-128">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cb651-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="cb651-129">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="cb651-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb651-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb651-130">Child Elements</span></span>  
  
|<span data-ttu-id="cb651-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb651-131">Element</span></span>|<span data-ttu-id="cb651-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb651-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb651-133">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="cb651-133">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="cb651-134">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb651-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="cb651-135">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="cb651-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb651-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb651-136">Parent Elements</span></span>  
  
|<span data-ttu-id="cb651-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb651-137">Element</span></span>|<span data-ttu-id="cb651-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb651-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb651-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb651-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="cb651-140">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb651-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb651-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb651-141">Remarks</span></span>  
 <span data-ttu-id="cb651-142">Kodlama bayt dizisi bir ileti dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="cb651-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="cb651-143">Kod çözme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="cb651-143">Decoding is the reverse process.</span></span> <span data-ttu-id="cb651-144">Bu işlemler karakter kodlamasını belirtim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cb651-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="cb651-145">`webMessageEncoding` Öğesi çalışır düz metin XML ve JSON Kodlamalar ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcılar için temsilci.</span><span class="sxs-lookup"><span data-stu-id="cb651-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="cb651-146">Bu temsilci bileşik ileti Kodlayıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cb651-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="cb651-147">Bu bağlama öğesi ve kendi bileşik Kodlayıcı tarafından kullanılan SOAP Mesajlaşma kullanmayın senaryolarda kodlama denetlemek için kullanılan `webHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb651-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="cb651-148">Bu senaryolar, "Düz eski XML" (POX), temsili durum aktarımı (REST), dağıtım, gerçekten basit dağıtım (RSS) ve Atom ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="cb651-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="cb651-149">Bileşik ileti Kodlayıcı SOAP veya WS adresleme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cb651-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="cb651-150">Bağlama öğesi bir yazma karakter kullanarak kodlama ile yapılandırılabilir `writeEncoding` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cb651-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="cb651-151">Sağlanan <xref:System.Text.Encoding> değeri JSON ve metin XML örnekleri için yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb651-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="cb651-152">Üzerinde okuma, tüm geçerli ileti kodlama ve metin kodlaması anladım.</span><span class="sxs-lookup"><span data-stu-id="cb651-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="cb651-153">`maxReadPoolSize` ve `maxWritePoolSize` okuyucuları ve yazıcıları sırasıyla ayrılacak en fazla sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb651-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="cb651-154">Varsayılan olarak, 64 okuyucuları ve 16 yazıcıları ayrılır.</span><span class="sxs-lookup"><span data-stu-id="cb651-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="cb651-155">Varsayılan karmaşıklık kısıtlamaları da ayarlanır kullanarak [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) öğesi (DOS) hizmet reddi sınıfının karşı korumak için uç nokta işlemeyi bağlamanın ileti karmaşıklık kullanmak için bu girişim saldırıları kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="cb651-155">Default complexity constraints are also set using the [\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb651-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb651-156">Example</span></span>  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb651-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb651-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="cb651-158">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="cb651-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="cb651-159">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="cb651-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="cb651-160">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb651-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cb651-161">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="cb651-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cb651-162">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb651-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cb651-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cb651-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
