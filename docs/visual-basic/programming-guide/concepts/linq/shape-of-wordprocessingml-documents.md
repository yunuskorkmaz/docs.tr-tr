---
title: Şekil WordprocessingML belgeleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 1ff5f0e42336e894f0ee808edb61661c1f850284
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231414"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="bb637-102">Şekil WordprocessingML belgeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb637-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="bb637-103">Bu konu WordprocessingML belge XML şeklini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="bb637-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="bb637-104">Microsoft Office biçimleri</span><span class="sxs-lookup"><span data-stu-id="bb637-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="bb637-105">Office Açık XML (Açık XML olarak bilinir) 2007 Microsoft Office sistemi için yerel dosya biçimidir.</span><span class="sxs-lookup"><span data-stu-id="bb637-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="bb637-106">Açık XML'dir biçimlendirmek XML tabanlı bir Ecma standardı ve şu anda ISO IEC standartları sürecinden.</span><span class="sxs-lookup"><span data-stu-id="bb637-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="bb637-107">Open XML içinde sözcük işleme dosyaları için biçimlendirme dili WordprocessingML adı verilir.</span><span class="sxs-lookup"><span data-stu-id="bb637-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="bb637-108">Bu öğretici WordprocessingML kaynak dosyaları örnekler için giriş olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb637-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="bb637-109">Microsoft Office 2003 kullanıyorsanız, Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi yüklü değilse, belgeleri Office Açık XML biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb637-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="bb637-110">Şekil WordprocessingML belgeleri</span><span class="sxs-lookup"><span data-stu-id="bb637-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="bb637-111">Şekil WordprocessingML belgelerin anlamak için ilk şeydir.</span><span class="sxs-lookup"><span data-stu-id="bb637-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="bb637-112">WordprocessingML belge body öğesi içeriyor (adlı `w:body`), belgenin paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="bb637-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="bb637-113">Bir veya daha fazla metin çalışıyor her paragraf içerir (adlı `w:r`).</span><span class="sxs-lookup"><span data-stu-id="bb637-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="bb637-114">Bir veya daha fazla metin parçaları çalıştırmak her metni içeren (adlı `w:t`).</span><span class="sxs-lookup"><span data-stu-id="bb637-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="bb637-115">Çok basit bir WordprocessingML belge verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bb637-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="bb637-116">Bu belge iki paragraf içeriyor.</span><span class="sxs-lookup"><span data-stu-id="bb637-116">This document contains two paragraphs.</span></span> <span data-ttu-id="bb637-117">Her ikisi de çalıştıran tek bir metin içermelidir ve tek bir metin parça çalıştırmak her metin içeriyor.</span><span class="sxs-lookup"><span data-stu-id="bb637-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="bb637-118">XML formundaki WordprocessingML belgesinin içeriğini görmek için en kolay yolu bir Microsoft Word kaydedin kullanarak ve ardından XML konsola yazdırır aşağıdaki programı çalıştırın oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="bb637-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="bb637-119">Bu örnek WindowsBase derlemesinde sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb637-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="bb637-120">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bb637-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="bb637-121">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bb637-121">External Resources</span></span>  
 <span data-ttu-id="bb637-122">[Office (2007) açık XML dosya biçimleri](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="bb637-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>  
  
 <span data-ttu-id="bb637-123">[WordprocessingML genel bakış](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="bb637-123">[Overview of WordprocessingML](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)</span></span>  
  
 [<span data-ttu-id="bb637-124">Office 2003: XML şemaları başvuru indirme sayfası</span><span class="sxs-lookup"><span data-stu-id="bb637-124">Office 2003: XML Reference Schemas Download page</span></span>](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="bb637-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb637-125">See Also</span></span>  
 [<span data-ttu-id="bb637-126">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb637-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
