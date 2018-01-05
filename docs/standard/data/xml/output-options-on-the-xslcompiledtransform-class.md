---
title: "Çıkış seçenekleri XslCompiledTransform sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84171c92a56a9970b5ffc16ce8f30c85d61cc678
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a><span data-ttu-id="b760a-102">Çıkış seçenekleri XslCompiledTransform sınıfı</span><span class="sxs-lookup"><span data-stu-id="b760a-102">Output Options on the XslCompiledTransform Class</span></span>
<span data-ttu-id="b760a-103">Bu konuda kullanılabilir XSLT çıkış seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b760a-103">This topic discusses the available XSLT output options.</span></span> <span data-ttu-id="b760a-104">Stil sayfası içinde veya üzerinde çıkış seçenekleri belirtebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b760a-104">You can specify output options in the style sheet, or on the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="xsloutput-element"></a><span data-ttu-id="b760a-105">önceliğiyle öğesi</span><span class="sxs-lookup"><span data-stu-id="b760a-105">xsl:output Element</span></span>  
 <span data-ttu-id="b760a-106">`xsl:output` Öğesi çıktı seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b760a-106">The `xsl:output` element specifies options for the output.</span></span> <span data-ttu-id="b760a-107">Belirtilen çıktı türü <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi davranışını belirler `xsl:output` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="b760a-107">The output type specified by the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method determines the behavior of the `xsl:output` options.</span></span>  
  
 <span data-ttu-id="b760a-108">Aşağıdaki tabloda, her kullanılabilir özniteliklerin davranışını tanımlar. `xsl:output` çıktı türü bir akış olduğunda öğesi veya <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="b760a-108">The following table describes the behavior for each of the attributes available on the `xsl:output` element when the output type is a stream or a <xref:System.IO.TextWriter>.</span></span>  
  
|<span data-ttu-id="b760a-109">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="b760a-109">Attribute name</span></span>|<span data-ttu-id="b760a-110">Davranış</span><span class="sxs-lookup"><span data-stu-id="b760a-110">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="b760a-111">yöntemi</span><span class="sxs-lookup"><span data-stu-id="b760a-111">method</span></span>|<span data-ttu-id="b760a-112">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-112">Supported.</span></span>|  
|<span data-ttu-id="b760a-113">sürüm</span><span class="sxs-lookup"><span data-stu-id="b760a-113">version</span></span>|<span data-ttu-id="b760a-114">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="b760a-114">Ignored.</span></span> <span data-ttu-id="b760a-115">Her zaman XML 1.0 ve HTML 4.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="b760a-115">The version is always 1.0 for XML and 4.0 for HTML.</span></span>|  
|<span data-ttu-id="b760a-116">encoding</span><span class="sxs-lookup"><span data-stu-id="b760a-116">encoding</span></span>|<span data-ttu-id="b760a-117">İçin alırken göz ardı bir <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="b760a-117">Ignored when outputting to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="b760a-118"><xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Özelliğinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b760a-118">The <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> property is used instead.</span></span>|  
|<span data-ttu-id="b760a-119">atlayın-xml-bildirimi</span><span class="sxs-lookup"><span data-stu-id="b760a-119">omit-xml-declaration</span></span>|<span data-ttu-id="b760a-120">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-120">Supported.</span></span>|  
|<span data-ttu-id="b760a-121">bağımsız</span><span class="sxs-lookup"><span data-stu-id="b760a-121">standalone</span></span>|<span data-ttu-id="b760a-122">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-122">Supported.</span></span>|  
|<span data-ttu-id="b760a-123">doctype-genel</span><span class="sxs-lookup"><span data-stu-id="b760a-123">doctype-public</span></span>|<span data-ttu-id="b760a-124">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-124">Supported.</span></span>|  
|<span data-ttu-id="b760a-125">Sistem dışı doctype</span><span class="sxs-lookup"><span data-stu-id="b760a-125">doctype-system</span></span>|<span data-ttu-id="b760a-126">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-126">Supported.</span></span>|  
|<span data-ttu-id="b760a-127">CDATA bölümü öğeleri</span><span class="sxs-lookup"><span data-stu-id="b760a-127">cdata-section-elements</span></span>|<span data-ttu-id="b760a-128">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-128">Supported.</span></span>|  
|<span data-ttu-id="b760a-129">Girinti</span><span class="sxs-lookup"><span data-stu-id="b760a-129">indent</span></span>|<span data-ttu-id="b760a-130">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-130">Supported.</span></span>|  
|<span data-ttu-id="b760a-131">medya türü</span><span class="sxs-lookup"><span data-stu-id="b760a-131">media-type</span></span>|<span data-ttu-id="b760a-132">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="b760a-132">Supported.</span></span>|  
  
#### <a name="sending-output-to-an-xmlwriter"></a><span data-ttu-id="b760a-133">Çıkış için bir XmlWriter gönderme</span><span class="sxs-lookup"><span data-stu-id="b760a-133">Sending Output to an XmlWriter</span></span>  
 <span data-ttu-id="b760a-134">Stil sayfası kullanıyorsa `xsl:output` öğesi ve çıkış türü bir <xref:System.Xml.XmlWriter> nesnesi, kullanmanız gereken <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> oluşturduğunuzda özelliği <xref:System.Xml.XmlWriter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b760a-134">If your style sheet uses the `xsl:output` element and the output type is an <xref:System.Xml.XmlWriter> object, you should use the <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> property when you create the <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="b760a-135"><xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Xml.XmlWriterSettings> bilgi içeren nesne türetilen `xsl:output` derlenmiş stil sayfası öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b760a-135">The <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> property returns an <xref:System.Xml.XmlWriterSettings> object that contains information derived from the `xsl:output` element of a compiled style sheet.</span></span> <span data-ttu-id="b760a-136">Bu <xref:System.Xml.XmlWriterSettings> nesne için geçirilebilir <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> yöntemi oluşturmak için bir <xref:System.Xml.XmlWriter> doğru ayarlarla nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b760a-136">This <xref:System.Xml.XmlWriterSettings> object can be passed to the <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> method to create an <xref:System.Xml.XmlWriter> object with the correct settings.</span></span>  
  
## <a name="output-types"></a><span data-ttu-id="b760a-137">Çıktı türleri</span><span class="sxs-lookup"><span data-stu-id="b760a-137">Output Types</span></span>  
 <span data-ttu-id="b760a-138">Kullanılabilir çıktı türleri aşağıdaki listede açıklanmaktadır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> komutu.</span><span class="sxs-lookup"><span data-stu-id="b760a-138">The following list describes the output types available on the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> command.</span></span>  
  
#### <a name="xmlwriter"></a><span data-ttu-id="b760a-139">XmlWriter</span><span class="sxs-lookup"><span data-stu-id="b760a-139">XmlWriter</span></span>  
 <span data-ttu-id="b760a-140"><xref:System.Xml.XmlWriter> Sınıfı XML akışları veya dosyaları yazar.</span><span class="sxs-lookup"><span data-stu-id="b760a-140">The <xref:System.Xml.XmlWriter> class writes out XML streams or files.</span></span> <span data-ttu-id="b760a-141">Destek almak için özellikleri belirtebilirsiniz <xref:System.Xml.XmlWriter> nesnesi kullanarak çıkış seçenekleri de dahil olmak üzere, <xref:System.Xml.XmlWriterSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b760a-141">You can specify the features to support on the <xref:System.Xml.XmlWriter> object, including output options, by using the <xref:System.Xml.XmlWriterSettings> class.</span></span> <span data-ttu-id="b760a-142"><xref:System.Xml.XmlWriter> Sınıftır bütünleyici <xref:System.Xml> framework.</span><span class="sxs-lookup"><span data-stu-id="b760a-142">The <xref:System.Xml.XmlWriter> class is an integral part of the <xref:System.Xml> framework.</span></span> <span data-ttu-id="b760a-143">Bu çıktı türü çıkış sonuçları kanalı başka bir XML işlemi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b760a-143">Use this output type to pipeline the output results into another XML process.</span></span>  
  
#### <a name="string"></a><span data-ttu-id="b760a-144">Dize</span><span class="sxs-lookup"><span data-stu-id="b760a-144">String</span></span>  
 <span data-ttu-id="b760a-145">Çıktı dosyası URI'sini belirtmek için bu çıktı türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b760a-145">Use this output type to specify the URI of the output file.</span></span>  
  
#### <a name="stream"></a><span data-ttu-id="b760a-146">Akış</span><span class="sxs-lookup"><span data-stu-id="b760a-146">Stream</span></span>  
 <span data-ttu-id="b760a-147">Bir dosya, bir giriş/çıkış cihaz, bir işlemler arası iletişim kanalı ya da bir TCP/IP'yi yuva gibi bayt dizisi için bir Özet akışıdır.</span><span class="sxs-lookup"><span data-stu-id="b760a-147">A stream is an abstraction of a sequence of bytes, such as a file, an input/output device, an inter-process communication pipe, or a TCP/IP socket.</span></span> <span data-ttu-id="b760a-148"><xref:System.IO.Stream> Sınıfı ve türetilmiş sınıflarının giriş ve çıkış, işletim sistemi ve arka plandaki cihazların belirli ayrıntıları Programcı yalıtma farklı bu tür genel bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="b760a-148">The <xref:System.IO.Stream> class and its derived classes provide a generic view of these different types of input and output, isolating the programmer from the specific details of the operating system and the underlying devices.</span></span>  
  
 <span data-ttu-id="b760a-149">Veri göndermesini Bu çıktı türü kullanan bir <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, veya bir çıktı akışına (`Response.OutputStream`).</span><span class="sxs-lookup"><span data-stu-id="b760a-149">Use this output type to send data to a <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, or an output stream (`Response.OutputStream`).</span></span>  
  
#### <a name="textwriter"></a><span data-ttu-id="b760a-150">TextWriter</span><span class="sxs-lookup"><span data-stu-id="b760a-150">TextWriter</span></span>  
 <span data-ttu-id="b760a-151"><xref:System.IO.TextWriter> Sıralı karakterleri yazar.</span><span class="sxs-lookup"><span data-stu-id="b760a-151">The <xref:System.IO.TextWriter> writes sequential characters.</span></span> <span data-ttu-id="b760a-152">Şu uygulanan <xref:System.IO.StringWriter> ve <xref:System.IO.StreamWriter> karakter dizeleri veya akışlar, sırasıyla yazma sınıfları.</span><span class="sxs-lookup"><span data-stu-id="b760a-152">It is implemented in the <xref:System.IO.StringWriter> and <xref:System.IO.StreamWriter> classes, which write characters to strings or streams, respectively.</span></span> <span data-ttu-id="b760a-153">Bir dizeyi çıktı istediğinizde bu çıktı türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b760a-153">Use this output type when you want to output to a string.</span></span>  
  
## <a name="notes"></a><span data-ttu-id="b760a-154">Notlar</span><span class="sxs-lookup"><span data-stu-id="b760a-154">Notes</span></span>  
  
-   <span data-ttu-id="b760a-155">Boş etiketleri yazarken, ters eğik çizgi, öğe adı son karakter arasında bir boşluk yazılır `<myElement />` örneğin.</span><span class="sxs-lookup"><span data-stu-id="b760a-155">When writing out empty tags, a space is written between the last character of the element name and the backslash, `<myElement />` for example.</span></span> <span data-ttu-id="b760a-156">Bu eski tarayıcılar oluşturulan HTML sayfaları doğru görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b760a-156">This lets older browsers display the generated HTML pages correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b760a-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b760a-157">See Also</span></span>  
 [<span data-ttu-id="b760a-158">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b760a-158">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
