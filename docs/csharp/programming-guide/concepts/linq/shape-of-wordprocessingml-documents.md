---
title: WordprocessingML belgelerinin şekli (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732678"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="1c333-102">WordprocessingML belgelerinin şekli (C#)</span><span class="sxs-lookup"><span data-stu-id="1c333-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="1c333-103">Bu konu, bir WordprocessingML belgesinin XML şeklini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="1c333-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="1c333-104">Microsoft Office biçimleri</span><span class="sxs-lookup"><span data-stu-id="1c333-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="1c333-105">2007 Microsoft Office sistemi için yerel dosya biçimi Office Open XML 'dir (genellikle Open XML olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="1c333-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="1c333-106">Open XML, bir ECMA Standard ve şu anda ISO-ıEC standartları sürecinden geçen XML tabanlı bir biçimdir.</span><span class="sxs-lookup"><span data-stu-id="1c333-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="1c333-107">Open XML içindeki sözcük işleme dosyalarının biçimlendirme dili WordprocessingML olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1c333-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="1c333-108">Bu öğretici, örnekler için giriş olarak WordprocessingML kaynak dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c333-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="1c333-109">Microsoft Office 2003 kullanıyorsanız Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk paketini yüklediyseniz Office Open XML biçimindeki belgeleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c333-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="1c333-110">WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="1c333-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="1c333-111">Anlaşılması gereken ilk şey WordprocessingML belgelerinin şekildir.</span><span class="sxs-lookup"><span data-stu-id="1c333-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="1c333-112">WordprocessingML belgesi, belgenin paragraflarını içeren bir body öğesi (`w:body`) içerir.</span><span class="sxs-lookup"><span data-stu-id="1c333-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="1c333-113">Her paragraf bir veya daha fazla metin çalıştırması (`w:r`adlı) içerir.</span><span class="sxs-lookup"><span data-stu-id="1c333-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="1c333-114">Her metin çalışması bir veya daha fazla metin parçası içerir (`w:t`olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="1c333-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="1c333-115">Aşağıda çok basit bir WordprocessingML belgesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1c333-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="1c333-116">Bu belge iki paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="1c333-116">This document contains two paragraphs.</span></span> <span data-ttu-id="1c333-117">Her ikisi de tek bir metin çalıştırması içerir ve her metin çalışması tek bir metin parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="1c333-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="1c333-118">XML biçiminde bir WordprocessingML belgesinin içeriğini görmenin en kolay yolu Microsoft Word 'Ü kullanarak bir tane oluşturmak, kaydetmeniz ve ardından XML 'i konsola yazdıran aşağıdaki programı çalıştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c333-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="1c333-119">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c333-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="1c333-120"><xref:System.IO.Packaging?displayProperty=nameWithType> ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c333-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="1c333-121">Dış kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1c333-121">External resources</span></span>

- [<span data-ttu-id="1c333-122">Office (2007) Open XML dosya biçimlerine giriş</span><span class="sxs-lookup"><span data-stu-id="1c333-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="1c333-123">WordprocessingML 'ye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c333-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="1c333-124">WordProcessingML dosyasının anatomi</span><span class="sxs-lookup"><span data-stu-id="1c333-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="1c333-125">WordprocessingML 'ye giriş</span><span class="sxs-lookup"><span data-stu-id="1c333-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="1c333-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c333-126">See also</span></span>

- [<span data-ttu-id="1c333-127">Öğretici: bir WordprocessingML belgesinde (C#) içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="1c333-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
