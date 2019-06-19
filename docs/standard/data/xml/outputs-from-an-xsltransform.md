---
title: XslTransform Çıkışları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 383cfbe72d89f4360692f002a7104f7ae0bc0bdc
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170870"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="34181-102">XslTransform Çıkışları</span><span class="sxs-lookup"><span data-stu-id="34181-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="34181-103">Stil sayfaları kullanıp çıkış biçimini belirlemek bu yana bir `<xsl:output>` deyimiyle `method` öznitelik, aşağıdaki tabloda açıklanmaktadır çıkış biçimini olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıkış biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="34181-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34181-104"><xref:System.Xml.Xsl.XslTransform> Sınıfı .NET Framework 2. 0'kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="34181-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="34181-105">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34181-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="34181-106">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="34181-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="34181-107">Stil sayfaları kullanıp çıkış biçimini belirlemek bu yana bir `<xsl:output>` deyimiyle `method` öznitelik, aşağıdaki tabloda açıklanmaktadır çıkış biçimini olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkışını yazmak için kullanılır ve çıkış biçimi olarak bildirilen bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="34181-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="34181-108">Aşağıdaki tabloda bir çıkış türü olarak bildirilmiş bıraktığınızda ne olacağı açıklanır <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi kullanımı ile birlikte bir `<xsl:output>` deyimi:</span><span class="sxs-lookup"><span data-stu-id="34181-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="34181-109">\<önceliğiyle yöntemi = > öznitelik</span><span class="sxs-lookup"><span data-stu-id="34181-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="34181-110">Sonuç biçimi</span><span class="sxs-lookup"><span data-stu-id="34181-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="34181-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="34181-111">method="xml"</span></span>|<span data-ttu-id="34181-112">XML</span><span class="sxs-lookup"><span data-stu-id="34181-112">XML</span></span>|  
|<span data-ttu-id="34181-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="34181-113">method="html"</span></span>|<span data-ttu-id="34181-114">HTML</span><span class="sxs-lookup"><span data-stu-id="34181-114">HTML</span></span>|  
|<span data-ttu-id="34181-115">yöntem = "text"</span><span class="sxs-lookup"><span data-stu-id="34181-115">method="text"</span></span>|<span data-ttu-id="34181-116">Metin</span><span class="sxs-lookup"><span data-stu-id="34181-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="34181-117">Not: `<xsl:output>` Deyimi göz ardı edilir olduğunda çıktısını <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="34181-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="34181-118">Aşağıdaki öznitelikler desteklenen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkış bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="34181-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="34181-119">kodlama \*</span><span class="sxs-lookup"><span data-stu-id="34181-119">encoding\*</span></span>  
  
- <span data-ttu-id="34181-120">atlayın-xml-bildirimi</span><span class="sxs-lookup"><span data-stu-id="34181-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="34181-121">bağımsız</span><span class="sxs-lookup"><span data-stu-id="34181-121">standalone</span></span>  
  
- <span data-ttu-id="34181-122">doctype-genel</span><span class="sxs-lookup"><span data-stu-id="34181-122">doctype-public</span></span>  
  
- <span data-ttu-id="34181-123">doctype sistem</span><span class="sxs-lookup"><span data-stu-id="34181-123">doctype-system</span></span>  
  
- <span data-ttu-id="34181-124">CDATA bölümünün öğeleri</span><span class="sxs-lookup"><span data-stu-id="34181-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="34181-125">Girintile</span><span class="sxs-lookup"><span data-stu-id="34181-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34181-126">\* kodlama özniteliği göz ardı edilir olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> çıktısını için gönderme yöntemi bir <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="34181-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="34181-127">Kodlama özelliği <xref:System.IO.TextWriter> yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34181-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="34181-128">Aşağıdaki özniteliği göz ardı edilir olduğunda <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çıkış bir <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="34181-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="34181-129">Sürüm: sürüm 1.0 her zaman olur.</span><span class="sxs-lookup"><span data-stu-id="34181-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="34181-130">medya türü: medya türü</span><span class="sxs-lookup"><span data-stu-id="34181-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="34181-131">Kaçış özel karakterleri</span><span class="sxs-lookup"><span data-stu-id="34181-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="34181-132">`<xsl:text disable-output-escaping>` Etiketi, özel karakterler bir XML forma çizgilerin aşağıdaki gibi ihtiyacınız olup olmadığını belirtmek için kullanılır (örneğin, kullanarak `<&lt>` yerine `"<"` sembol) veya mevcut koşulunda sol.</span><span class="sxs-lookup"><span data-stu-id="34181-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="34181-133">`disable-output-escaping` Özniteliği yok sayıldı için dönüştürürken bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesne ve özel karakterler üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="34181-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34181-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34181-134">See also</span></span>

- [<span data-ttu-id="34181-135">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="34181-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
