---
title: "Bir çok çıkışlarından"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92bf2d7184ca2eb8b17c1d83130c66d1f33f0483
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="55fe9-102">Bir çok çıkışlarından</span><span class="sxs-lookup"><span data-stu-id="55fe9-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="55fe9-103">Stil sayfaları çıktı biçimi kullanarak belirleyebilirsiniz bu yana bir `<xsl:output>` deyimiyle `method` özniteliği, aşağıdaki tabloda açıklanmaktadır çıkış biçimi olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıktı biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="55fe9-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55fe9-104"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55fe9-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="55fe9-105">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="55fe9-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="55fe9-106">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="55fe9-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="55fe9-107">Stil sayfaları çıktı biçimi kullanarak belirleyebilirsiniz bu yana bir `<xsl:output>` deyimiyle `method` özniteliği, aşağıdaki tabloda açıklanmaktadır çıkış biçimi olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıktı biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="55fe9-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="55fe9-108">Aşağıdaki tabloda bir çıktı türü olarak bildirilmiş ne olur açıklanmaktadır <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi kullanımı ile birlikte bir `<xsl:output>` deyimi:</span><span class="sxs-lookup"><span data-stu-id="55fe9-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="55fe9-109">\<önceliğiyle yöntemi = > özniteliği</span><span class="sxs-lookup"><span data-stu-id="55fe9-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="55fe9-110">Sonuç biçimi</span><span class="sxs-lookup"><span data-stu-id="55fe9-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="55fe9-111">yöntem = "xml"</span><span class="sxs-lookup"><span data-stu-id="55fe9-111">method="xml"</span></span>|<span data-ttu-id="55fe9-112">XML</span><span class="sxs-lookup"><span data-stu-id="55fe9-112">XML</span></span>|  
|<span data-ttu-id="55fe9-113">yöntem = "html"</span><span class="sxs-lookup"><span data-stu-id="55fe9-113">method="html"</span></span>|<span data-ttu-id="55fe9-114">HTML</span><span class="sxs-lookup"><span data-stu-id="55fe9-114">HTML</span></span>|  
|<span data-ttu-id="55fe9-115">yöntem = "text"</span><span class="sxs-lookup"><span data-stu-id="55fe9-115">method="text"</span></span>|<span data-ttu-id="55fe9-116">Metin</span><span class="sxs-lookup"><span data-stu-id="55fe9-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="55fe9-117">Not: `<xsl:output>` deyimi göz ardı edilir zaman çıktısını <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="55fe9-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="55fe9-118">Aşağıdaki öznitelikler desteklenen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısı bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="55fe9-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="55fe9-119">kodlama *</span><span class="sxs-lookup"><span data-stu-id="55fe9-119">encoding*</span></span>  
  
-   <span data-ttu-id="55fe9-120">atlayın-xml-bildirimi</span><span class="sxs-lookup"><span data-stu-id="55fe9-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="55fe9-121">bağımsız</span><span class="sxs-lookup"><span data-stu-id="55fe9-121">standalone</span></span>  
  
-   <span data-ttu-id="55fe9-122">doctype-genel</span><span class="sxs-lookup"><span data-stu-id="55fe9-122">doctype-public</span></span>  
  
-   <span data-ttu-id="55fe9-123">Sistem dışı doctype</span><span class="sxs-lookup"><span data-stu-id="55fe9-123">doctype-system</span></span>  
  
-   <span data-ttu-id="55fe9-124">CDATA bölümü öğeleri</span><span class="sxs-lookup"><span data-stu-id="55fe9-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="55fe9-125">Girinti</span><span class="sxs-lookup"><span data-stu-id="55fe9-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55fe9-126">* kodlama özniteliği göz ardı zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısını için gönderme bir <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="55fe9-126">*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="55fe9-127">Kodlama özelliği <xref:System.IO.TextWriter> onun yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55fe9-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="55fe9-128">Aşağıdaki öznitelik yoksayılır zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıktısı bir <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="55fe9-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="55fe9-129">Sürüm: sürümüdür 1.0 her zaman</span><span class="sxs-lookup"><span data-stu-id="55fe9-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="55fe9-130">Media-type: medya türü</span><span class="sxs-lookup"><span data-stu-id="55fe9-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="55fe9-131">Kaçış özel karakterleri</span><span class="sxs-lookup"><span data-stu-id="55fe9-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="55fe9-132">`<xsl:text disable-output-escaping>` Etiketi özel karakterler bir XML forma kaçış gerek olmadığını belirtmek için kullanılır (örneğin, kullanarak `<&lt>` yerine `"<"` simgesi) veya mevcut koşulunda sol.</span><span class="sxs-lookup"><span data-stu-id="55fe9-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="55fe9-133">`disable-output-escaping` Özniteliği göz ardı edilir için dönüştürülürken bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesne ve özel karakterler üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="55fe9-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fe9-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55fe9-134">See Also</span></span>  
 [<span data-ttu-id="55fe9-135">XSLT işlemci çok sınıfı uygular</span><span class="sxs-lookup"><span data-stu-id="55fe9-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
