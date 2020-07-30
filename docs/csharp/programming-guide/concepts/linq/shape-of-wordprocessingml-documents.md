---
title: WordprocessingML belgelerinin şekli (C#)
description: WordprocessingML belgesinin biçimi hakkında bilgi edinin. Birçok C# örneği WordprocessingML belgesi kullanır.
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 4a7716d775a634c5ad3719714be68fce67d5cbfe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302353"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="3104b-104">WordprocessingML belgelerinin şekli (C#)</span><span class="sxs-lookup"><span data-stu-id="3104b-104">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="3104b-105">Bu konu, bir WordprocessingML belgesinin XML şeklini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="3104b-105">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="3104b-106">Microsoft Office biçimleri</span><span class="sxs-lookup"><span data-stu-id="3104b-106">Microsoft Office Formats</span></span>  
 <span data-ttu-id="3104b-107">2007 Microsoft Office sistemi için yerel dosya biçimi Office Open XML 'dir (genellikle Open XML olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="3104b-107">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="3104b-108">Open XML, bir ECMA Standard ve şu anda ISO-ıEC standartları sürecinden geçen XML tabanlı bir biçimdir.</span><span class="sxs-lookup"><span data-stu-id="3104b-108">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="3104b-109">Open XML içindeki sözcük işleme dosyalarının biçimlendirme dili WordprocessingML olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3104b-109">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="3104b-110">Bu öğretici, örnekler için giriş olarak WordprocessingML kaynak dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3104b-110">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="3104b-111">Microsoft Office 2003 kullanıyorsanız Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk paketini yüklediyseniz Office Open XML biçimindeki belgeleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3104b-111">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="3104b-112">WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="3104b-112">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="3104b-113">Anlaşılması gereken ilk şey WordprocessingML belgelerinin şekildir.</span><span class="sxs-lookup"><span data-stu-id="3104b-113">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="3104b-114">WordprocessingML belgesi, belgenin paragraflarını içeren bir body öğesi (adlandırılmış `w:body` ) içerir.</span><span class="sxs-lookup"><span data-stu-id="3104b-114">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="3104b-115">Her paragraf bir veya daha fazla metin çalıştırması (adlandırılmış `w:r` ) içerir.</span><span class="sxs-lookup"><span data-stu-id="3104b-115">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="3104b-116">Her metin çalışması bir veya daha fazla metin parçası (adlandırılmış `w:t` ) içerir.</span><span class="sxs-lookup"><span data-stu-id="3104b-116">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="3104b-117">Aşağıda çok basit bir WordprocessingML belgesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3104b-117">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="3104b-118">Bu belge iki paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="3104b-118">This document contains two paragraphs.</span></span> <span data-ttu-id="3104b-119">Her ikisi de tek bir metin çalıştırması içerir ve her metin çalışması tek bir metin parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="3104b-119">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="3104b-120">XML biçiminde bir WordprocessingML belgesinin içeriğini görmenin en kolay yolu Microsoft Word 'Ü kullanarak bir tane oluşturmak, kaydetmeniz ve ardından XML 'i konsola yazdıran aşağıdaki programı çalıştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3104b-120">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="3104b-121">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3104b-121">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="3104b-122"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3104b-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="3104b-123">Dış kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3104b-123">External resources</span></span>

- [<span data-ttu-id="3104b-124">Office (2007) Open XML dosya biçimlerine giriş</span><span class="sxs-lookup"><span data-stu-id="3104b-124">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="3104b-125">WordprocessingML 'ye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3104b-125">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="3104b-126">WordProcessingML dosyasının anatomi</span><span class="sxs-lookup"><span data-stu-id="3104b-126">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="3104b-127">WordprocessingML 'ye giriş</span><span class="sxs-lookup"><span data-stu-id="3104b-127">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="3104b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3104b-128">See also</span></span>

- [<span data-ttu-id="3104b-129">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="3104b-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
