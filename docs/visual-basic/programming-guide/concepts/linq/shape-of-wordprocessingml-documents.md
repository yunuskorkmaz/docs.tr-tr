---
title: (Visual Basic) WordprocessingML belgelerinin şekli
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 265da66329128e610c491c3ff50cec1bca434f6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786431"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="101fb-102">(Visual Basic) WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="101fb-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="101fb-103">Bu konu, WordprocessingML belgesinin XML şeklini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="101fb-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="101fb-104">Microsoft Office biçimleri</span><span class="sxs-lookup"><span data-stu-id="101fb-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="101fb-105">Office Open XML (Open XML yaygın olarak adlandırılır) 2007 Microsoft Office sistemi için yerel dosya biçimidir.</span><span class="sxs-lookup"><span data-stu-id="101fb-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="101fb-106">Açık XML'dir biçimi XML tabanlı bir Ecma standart ve şu anda ISO IEC standartları sürecinden.</span><span class="sxs-lookup"><span data-stu-id="101fb-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="101fb-107">Open XML içinde sözcük işleme dosyaları için biçimlendirme dili WordprocessingML çağrılır.</span><span class="sxs-lookup"><span data-stu-id="101fb-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="101fb-108">Bu öğreticide WordprocessingML kaynak dosyaları örnekler için giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="101fb-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="101fb-109">Microsoft Office 2003 kullanıyorsanız, Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi yüklediyseniz, belgeleri Office Open XML biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="101fb-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="101fb-110">WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="101fb-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="101fb-111">WordprocessingML belgelerinin şekli anlamak için ilk şeydir.</span><span class="sxs-lookup"><span data-stu-id="101fb-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="101fb-112">WordprocessingML belgesinin gövde öğesi içeren (adlı `w:body`) belgenin paragrafları içeren.</span><span class="sxs-lookup"><span data-stu-id="101fb-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="101fb-113">Her bir paragrafına içeren bir veya daha fazla metin çalışıyor (adlı `w:r`).</span><span class="sxs-lookup"><span data-stu-id="101fb-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="101fb-114">Çalıştıran her metin içeren bir veya daha fazla metin parçaları (adlı `w:t`).</span><span class="sxs-lookup"><span data-stu-id="101fb-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="101fb-115">Çok basit WordprocessingML belgesinin verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="101fb-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="101fb-116">Bu belge, iki paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="101fb-116">This document contains two paragraphs.</span></span> <span data-ttu-id="101fb-117">Her ikisi de çalıştıran tek bir metin içeren ve tek bir metin parçası çalıştırmak her metin içerir.</span><span class="sxs-lookup"><span data-stu-id="101fb-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="101fb-118">XML formundaki WordprocessingML belgesinin içeriğini görmek için en kolay yolu bir Microsoft Word kaydedin kullanarak ve ardından XML konsola yazdırır aşağıdaki programı çalıştırın oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="101fb-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="101fb-119">Bu örnekte WindowsBase derlemede bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="101fb-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="101fb-120">Türleri kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="101fb-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="101fb-121">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="101fb-121">External Resources</span></span>  
 <span data-ttu-id="101fb-122">[Office (2007) açık XML dosya biçimleri](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="101fb-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>  
  
 <span data-ttu-id="101fb-123">[WordprocessingML genel bakış](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span><span class="sxs-lookup"><span data-stu-id="101fb-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>  
  
 [<span data-ttu-id="101fb-124">Office 2003: XML şemaları başvuru indirme sayfası</span><span class="sxs-lookup"><span data-stu-id="101fb-124">Office 2003: XML Reference Schemas Download page</span></span>](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="101fb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="101fb-125">See also</span></span>

- [<span data-ttu-id="101fb-126">Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="101fb-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
