---
title: XslTransform Çıkışları
ms.date: 03/30/2017
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 765f6f9a91cc44a55ab0d66ed71f19f60ef81a56
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830070"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="e518a-102">XslTransform Çıkışları</span><span class="sxs-lookup"><span data-stu-id="e518a-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="e518a-103">Stil sayfaları, özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden `<xsl:output>` `method` , aşağıdaki tabloda çıktı biçiminin <xref:System.Xml.Xsl.XslTransform.Transform%2A> çıktıyı yazmak için ne zaman kullanıldığı ve çıkış biçiminin de veya olarak bildirildiği açıklanmaktadır <xref:System.IO.Stream> <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="e518a-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e518a-104"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e518a-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="e518a-105">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="e518a-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e518a-106">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="e518a-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="e518a-107">Stil sayfaları, özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden `<xsl:output>` `method` , aşağıdaki tabloda çıktı biçiminin <xref:System.Xml.Xsl.XslTransform.Transform%2A> çıktıyı yazmak için ne zaman kullanıldığı ve çıkış biçiminin de veya olarak bildirildiği açıklanmaktadır <xref:System.IO.Stream> <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="e518a-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="e518a-108">Aşağıdaki tabloda, bir çıkış türü <xref:System.Xml.Xsl.XslTransform.Transform%2A> bir deyimin kullanımıyla birlikte yöntemi tarafından bildirildiğinde ne olacağı açıklanmaktadır `<xsl:output>` :</span><span class="sxs-lookup"><span data-stu-id="e518a-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="e518a-109">\<xsl:output method = > özniteliği</span><span class="sxs-lookup"><span data-stu-id="e518a-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="e518a-110">Sonuç biçimi</span><span class="sxs-lookup"><span data-stu-id="e518a-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="e518a-111">method = "xml"</span><span class="sxs-lookup"><span data-stu-id="e518a-111">method="xml"</span></span>|<span data-ttu-id="e518a-112">XML</span><span class="sxs-lookup"><span data-stu-id="e518a-112">XML</span></span>|  
|<span data-ttu-id="e518a-113">method = "html"</span><span class="sxs-lookup"><span data-stu-id="e518a-113">method="html"</span></span>|<span data-ttu-id="e518a-114">HTML</span><span class="sxs-lookup"><span data-stu-id="e518a-114">HTML</span></span>|  
|<span data-ttu-id="e518a-115">method = "metin"</span><span class="sxs-lookup"><span data-stu-id="e518a-115">method="text"</span></span>|<span data-ttu-id="e518a-116">Metin</span><span class="sxs-lookup"><span data-stu-id="e518a-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e518a-117">Note: `<xsl:output>` yöntemin çıktısı bir veya olduğunda, ifade yok sayılır <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e518a-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="e518a-118">Aşağıdaki öznitelikler, <xref:System.Xml.Xsl.XslTransform.Transform%2A> ya da yöntem çıktısı bir veya olduğunda desteklenir <xref:System.IO.Stream> <xref:System.IO.TextWriter> :</span><span class="sxs-lookup"><span data-stu-id="e518a-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="e518a-119">şifreleme</span><span class="sxs-lookup"><span data-stu-id="e518a-119">encoding\*</span></span>  
  
- <span data-ttu-id="e518a-120">XML bildirimini atla</span><span class="sxs-lookup"><span data-stu-id="e518a-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="e518a-121">bağımsız</span><span class="sxs-lookup"><span data-stu-id="e518a-121">standalone</span></span>  
  
- <span data-ttu-id="e518a-122">doctype-genel</span><span class="sxs-lookup"><span data-stu-id="e518a-122">doctype-public</span></span>  
  
- <span data-ttu-id="e518a-123">DOCTYPE-System</span><span class="sxs-lookup"><span data-stu-id="e518a-123">doctype-system</span></span>  
  
- <span data-ttu-id="e518a-124">CDATA-bölüm-öğeler</span><span class="sxs-lookup"><span data-stu-id="e518a-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="e518a-125">leyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="e518a-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e518a-126">\*<xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntem, çıkışını bir öğesine gönderirken kodlama özniteliği yok sayılır <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="e518a-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="e518a-127"><xref:System.IO.TextWriter>Bunun yerine kodlama özelliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e518a-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="e518a-128">Aşağıdaki öznitelik, <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntem çıktısı bir olduğunda yok sayılır <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="e518a-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="e518a-129">Sürüm: sürüm her zaman 1,0</span><span class="sxs-lookup"><span data-stu-id="e518a-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="e518a-130">medya-türü: medya türü</span><span class="sxs-lookup"><span data-stu-id="e518a-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="e518a-131">Özel karakterleri kaçış</span><span class="sxs-lookup"><span data-stu-id="e518a-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="e518a-132">`<xsl:text disable-output-escaping>`Etiketi, özel karakterlerin BIR XML biçimine (örneğin, `<&lt>` simgenin yerine kullanılması) veya mevcut koşulda sola atlanıp atlanmayacağını belirtmek için kullanılır `"<"` .</span><span class="sxs-lookup"><span data-stu-id="e518a-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="e518a-133">`disable-output-escaping`Özniteliği bir veya nesnesine dönüştürülürken yok sayılır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> ve özel karakterler üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="e518a-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e518a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e518a-134">See also</span></span>

- [<span data-ttu-id="e518a-135">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="e518a-135">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
