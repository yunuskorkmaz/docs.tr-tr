---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: eddda5e805d7e2cc361b6925d34d13eb8fd614f9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385400"
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="ae71f-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="ae71f-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="ae71f-103">Düz metin XML'i, JavaScript nesne gösterimi (JSON) ileti Kodlamalar ve okunabilir ve bir Windows Communication Foundation (WCF) bağlaması içinde kullanıldığında yazılan için "ham" ikili içeriğin sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae71f-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="ae71f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae71f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ae71f-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ae71f-105">\<bindings></span></span>  
<span data-ttu-id="ae71f-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ae71f-106">\<customBinding></span></span>  
<span data-ttu-id="ae71f-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ae71f-107">\<binding></span></span>  
<span data-ttu-id="ae71f-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="ae71f-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae71f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae71f-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae71f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae71f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ae71f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae71f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae71f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae71f-112">Attributes</span></span>  
  
|<span data-ttu-id="ae71f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae71f-113">Attribute</span></span>|<span data-ttu-id="ae71f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae71f-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="ae71f-115">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="ae71f-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="ae71f-116">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="ae71f-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ae71f-117">Her iç kodlayıcılarda (yalnızca metin, JSON ve "ham") için 64 okuyucular varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ae71f-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="ae71f-118">Bu sayı arttıkça bellek tüketimi artırılması, ancak yenilerini oluşturmak yerine, önceden oluşturulan okuyucular havuzundan kullanmanız mümkün olduğundan, gelen iletilerin ani artışları ile dağıtılacak Kodlayıcı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="ae71f-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="ae71f-119">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="ae71f-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="ae71f-120">Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="ae71f-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ae71f-121">Her iç kodlayıcılarda (yalnızca metin, JSON ve "ham") için 16 yazıcılar varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ae71f-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="ae71f-122">Bu sayı arttıkça bellek tüketimi artırılması, ancak yenilerini oluşturmak yerine, önceden oluşturulan yazıcılar havuzundan kullanmanız mümkün olduğundan, giden iletilerin ani artışları ile uğraşmak için Kodlayıcı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="ae71f-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="ae71f-123">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ae71f-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ae71f-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="ae71f-125">-UnicodeFffeTextEncoding: Unicode büyük Endian'ya kodlaması.</span><span class="sxs-lookup"><span data-stu-id="ae71f-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="ae71f-126">-Utf16TextEncoding: Unicode kodlaması.</span><span class="sxs-lookup"><span data-stu-id="ae71f-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="ae71f-127">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="ae71f-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="ae71f-128">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ae71f-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="ae71f-129">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ae71f-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae71f-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae71f-130">Child Elements</span></span>  
  
|<span data-ttu-id="ae71f-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae71f-131">Element</span></span>|<span data-ttu-id="ae71f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae71f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae71f-133">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="ae71f-133">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="ae71f-134">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae71f-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ae71f-135">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ae71f-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae71f-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae71f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ae71f-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae71f-137">Element</span></span>|<span data-ttu-id="ae71f-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae71f-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae71f-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ae71f-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ae71f-140">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae71f-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae71f-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae71f-141">Remarks</span></span>  
 <span data-ttu-id="ae71f-142">Kodlama bir ileti bir dizi bayta dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="ae71f-143">Kod çözme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-143">Decoding is the reverse process.</span></span> <span data-ttu-id="ae71f-144">Bu işlemler, bir karakter kodlaması belirtimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="ae71f-145">`webMessageEncoding` Düz metin XML ve JSON Kodlamalar ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcılar için temsilci atayarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="ae71f-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="ae71f-146">Bu temsilci bileşik ileti Kodlayıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="ae71f-147">Bu bağlama öğesi ve kendi bileşik Kodlayıcı tarafından kullanılan SOAP ileti kullanmayan senaryolarda kodlama denetlemek için kullanılan `webHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ae71f-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="ae71f-148">Bu senaryolar, "Düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtım ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="ae71f-149">Bileşik ileti Kodlayıcı SOAP veya WS-Addressing desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ae71f-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="ae71f-150">Bağlama öğesi, bir yazma karakter kullanarak kodlaması ile yapılandırılabilir `writeEncoding` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ae71f-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="ae71f-151">Sağlanan <xref:System.Text.Encoding> değeri JSON ve XML metinsel çalışmalarının yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="ae71f-152">Okuma sırasında tüm geçerli ileti kodlama ve metin kodlaması anladım.</span><span class="sxs-lookup"><span data-stu-id="ae71f-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="ae71f-153">`maxReadPoolSize` ve `maxWritePoolSize` okuyucular ve yazıcılar sırasıyla ayrılacak en fazla sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae71f-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="ae71f-154">Varsayılan olarak, 64 okuyucular ve yazıcılar 16 ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ae71f-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="ae71f-155">Varsayılan karmaşıklığı kısıtlamaları, kullanılarak da ayarlanır [ \<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) öğesi bir sınıf hizmet (DOS) reddi karşı korumak için uç nokta işlemeyi bağlamak için ileti karmaşıklığı kullanmak için bu girişim saldırıları kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="ae71f-155">Default complexity constraints are also set using the [\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae71f-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae71f-156">Example</span></span>  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae71f-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae71f-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="ae71f-158">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="ae71f-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="ae71f-159">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="ae71f-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="ae71f-160">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ae71f-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ae71f-161">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ae71f-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ae71f-162">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ae71f-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ae71f-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ae71f-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
