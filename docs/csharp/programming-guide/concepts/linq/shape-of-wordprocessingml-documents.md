---
title: (C#) WordprocessingML belgelerinin şekli
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: f91e324e14e7cb3bb3912ebfab78daba71d5aae8
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052223"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="52e50-102">(C#) WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="52e50-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="52e50-103">Bu konu, WordprocessingML belgesinin XML şeklini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="52e50-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="52e50-104">Microsoft Office biçimleri</span><span class="sxs-lookup"><span data-stu-id="52e50-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="52e50-105">Office Open XML (Open XML yaygın olarak adlandırılır) 2007 Microsoft Office sistemi için yerel dosya biçimidir.</span><span class="sxs-lookup"><span data-stu-id="52e50-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="52e50-106">Açık XML'dir biçimi XML tabanlı bir Ecma standart ve şu anda ISO IEC standartları sürecinden.</span><span class="sxs-lookup"><span data-stu-id="52e50-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="52e50-107">Open XML içinde sözcük işleme dosyaları için biçimlendirme dili WordprocessingML çağrılır.</span><span class="sxs-lookup"><span data-stu-id="52e50-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="52e50-108">Bu öğreticide WordprocessingML kaynak dosyaları örnekler için giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52e50-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="52e50-109">Microsoft Office 2003 kullanıyorsanız, Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi yüklediyseniz, belgeleri Office Open XML biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e50-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="52e50-110">WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="52e50-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="52e50-111">WordprocessingML belgelerinin şekli anlamak için ilk şeydir.</span><span class="sxs-lookup"><span data-stu-id="52e50-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="52e50-112">WordprocessingML belgesinin gövde öğesi içeren (adlı `w:body`) belgenin paragrafları içeren.</span><span class="sxs-lookup"><span data-stu-id="52e50-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="52e50-113">Her bir paragrafına içeren bir veya daha fazla metin çalışıyor (adlı `w:r`).</span><span class="sxs-lookup"><span data-stu-id="52e50-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="52e50-114">Çalıştıran her metin içeren bir veya daha fazla metin parçaları (adlı `w:t`).</span><span class="sxs-lookup"><span data-stu-id="52e50-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="52e50-115">Çok basit WordprocessingML belgesinin verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="52e50-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="52e50-116">Bu belge, iki paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="52e50-116">This document contains two paragraphs.</span></span> <span data-ttu-id="52e50-117">Her ikisi de çalıştıran tek bir metin içeren ve tek bir metin parçası çalıştırmak her metin içerir.</span><span class="sxs-lookup"><span data-stu-id="52e50-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="52e50-118">XML formundaki WordprocessingML belgesinin içeriğini görmek için en kolay yolu bir Microsoft Word kaydedin kullanarak ve ardından XML konsola yazdırır aşağıdaki programı çalıştırın oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="52e50-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="52e50-119">Bu örnekte WindowsBase derlemede bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="52e50-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="52e50-120">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="52e50-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="52e50-121">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="52e50-121">External Resources</span></span>  
 [<span data-ttu-id="52e50-122">Office (2007) açık XML dosya biçimleri</span><span class="sxs-lookup"><span data-stu-id="52e50-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)  
 [<span data-ttu-id="52e50-123">WordprocessingML genel bakış</span><span class="sxs-lookup"><span data-stu-id="52e50-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)  
 [<span data-ttu-id="52e50-124">WordProcessingML dosya anatomisi</span><span class="sxs-lookup"><span data-stu-id="52e50-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="52e50-125">WordprocessingML giriş</span><span class="sxs-lookup"><span data-stu-id="52e50-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="52e50-126">Office 2003: XML şemaları başvuru indirme sayfası</span><span class="sxs-lookup"><span data-stu-id="52e50-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="52e50-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52e50-127">See also</span></span>

- [<span data-ttu-id="52e50-128">Öğretici: WordprocessingML belgesindeki içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="52e50-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
