---
title: XslTransform Çıkışları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6c2ea2fe2f02dc1897cb1348f4c2585b730036
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924963"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="3a90c-102">XslTransform Çıkışları</span><span class="sxs-lookup"><span data-stu-id="3a90c-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="3a90c-103">Stil sayfaları, `<xsl:output>` `method` özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> kullanıldığı ve çıkış biçiminin <xref:System.IO.Stream> veya<xref:System.IO.TextWriter>olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a90c-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a90c-104"><xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3a90c-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="3a90c-105"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a90c-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="3a90c-106">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="3a90c-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="3a90c-107">Stil sayfaları, `<xsl:output>` `method` özniteliği olan bir ifade kullanarak çıkış biçimini belirleyebildiğinden, aşağıdaki tabloda çıktı biçiminin çıktıyı yazmak için ne zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> kullanıldığı ve çıkış biçiminin <xref:System.IO.Stream> veya<xref:System.IO.TextWriter>olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a90c-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="3a90c-108">Aşağıdaki tabloda, bir çıkış türü bir <xref:System.Xml.Xsl.XslTransform.Transform%2A> `<xsl:output>` deyimin kullanımıyla birlikte yöntemi tarafından bildirildiğinde ne olacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="3a90c-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="3a90c-109">\<xsl: output yöntemi = > özniteliği</span><span class="sxs-lookup"><span data-stu-id="3a90c-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="3a90c-110">Sonuç biçimi</span><span class="sxs-lookup"><span data-stu-id="3a90c-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="3a90c-111">method = "xml"</span><span class="sxs-lookup"><span data-stu-id="3a90c-111">method="xml"</span></span>|<span data-ttu-id="3a90c-112">XML</span><span class="sxs-lookup"><span data-stu-id="3a90c-112">XML</span></span>|  
|<span data-ttu-id="3a90c-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="3a90c-113">method="html"</span></span>|<span data-ttu-id="3a90c-114">HTML</span><span class="sxs-lookup"><span data-stu-id="3a90c-114">HTML</span></span>|  
|<span data-ttu-id="3a90c-115">method = "metin"</span><span class="sxs-lookup"><span data-stu-id="3a90c-115">method="text"</span></span>|<span data-ttu-id="3a90c-116">Metin</span><span class="sxs-lookup"><span data-stu-id="3a90c-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3a90c-117">Not: Yöntemi, <xref:System.Xml.XmlReader> yönteminin çıktısı birveya<xref:System.Xml.XmlWriter>olduğunda yoksayılır. `<xsl:output>` <xref:System.Xml.Xsl.XslTransform.Transform%2A></span><span class="sxs-lookup"><span data-stu-id="3a90c-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="3a90c-118">Aşağıdaki öznitelikler, ya da <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntem çıktısı bir <xref:System.IO.Stream> veya <xref:System.IO.TextWriter>olduğunda desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3a90c-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="3a90c-119">şifreleme</span><span class="sxs-lookup"><span data-stu-id="3a90c-119">encoding\*</span></span>  
  
- <span data-ttu-id="3a90c-120">XML bildirimini atla</span><span class="sxs-lookup"><span data-stu-id="3a90c-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="3a90c-121">bağımsız</span><span class="sxs-lookup"><span data-stu-id="3a90c-121">standalone</span></span>  
  
- <span data-ttu-id="3a90c-122">doctype-genel</span><span class="sxs-lookup"><span data-stu-id="3a90c-122">doctype-public</span></span>  
  
- <span data-ttu-id="3a90c-123">DOCTYPE-System</span><span class="sxs-lookup"><span data-stu-id="3a90c-123">doctype-system</span></span>  
  
- <span data-ttu-id="3a90c-124">CDATA-bölüm-öğeler</span><span class="sxs-lookup"><span data-stu-id="3a90c-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="3a90c-125">leyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="3a90c-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3a90c-126">\*<xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntem, çıkışını bir <xref:System.IO.TextWriter>öğesine gönderirken kodlama özniteliği yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="3a90c-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="3a90c-127">Bunun yerine kodlama özelliği <xref:System.IO.TextWriter> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a90c-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span> 
  
 <span data-ttu-id="3a90c-128">Aşağıdaki öznitelik, <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntem çıktısı bir <xref:System.IO.Stream>olduğunda yok sayılır:</span><span class="sxs-lookup"><span data-stu-id="3a90c-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="3a90c-129">Sürüm: sürüm her zaman 1,0</span><span class="sxs-lookup"><span data-stu-id="3a90c-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="3a90c-130">medya-türü: medya türü</span><span class="sxs-lookup"><span data-stu-id="3a90c-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="3a90c-131">Özel karakterleri kaçış</span><span class="sxs-lookup"><span data-stu-id="3a90c-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="3a90c-132">Etiketi, özel karakterlerin bir XML biçimine (örneğin, `"<"` simgenin yerine kullanılması `<&lt>` ) veya mevcut koşulda sola atlanıp atlanmayacağını belirtmek için kullanılır. `<xsl:text disable-output-escaping>`</span><span class="sxs-lookup"><span data-stu-id="3a90c-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="3a90c-133">Özniteliği bir <xref:System.Xml.XmlReader> veya<xref:System.Xml.XmlWriter> nesnesine dönüştürülürken yok sayılır ve özel karakterler üzerinde hiçbir etkisi olmaz. `disable-output-escaping`</span><span class="sxs-lookup"><span data-stu-id="3a90c-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a90c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a90c-134">See also</span></span>

- [<span data-ttu-id="3a90c-135">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="3a90c-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
