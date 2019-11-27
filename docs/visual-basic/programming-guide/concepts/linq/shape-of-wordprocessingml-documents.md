---
title: WordprocessingML Belgelerinin Şekli
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 64e9ca280c000ba488bfc72248bd83e37474f043
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350601"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="71acb-102">WordprocessingML belgelerinin şekli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71acb-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="71acb-103">Bu konu, bir WordprocessingML belgesinin XML şeklini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="71acb-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="71acb-104">Microsoft Office biçimleri</span><span class="sxs-lookup"><span data-stu-id="71acb-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="71acb-105">2007 Microsoft Office sistemi için yerel dosya biçimi Office Open XML 'dir (genellikle Open XML olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="71acb-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="71acb-106">Open XML, bir ECMA Standard ve şu anda ISO-ıEC standartları sürecinden geçen XML tabanlı bir biçimdir.</span><span class="sxs-lookup"><span data-stu-id="71acb-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="71acb-107">Open XML içindeki sözcük işleme dosyalarının biçimlendirme dili WordprocessingML olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="71acb-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="71acb-108">Bu öğretici, örnekler için giriş olarak WordprocessingML kaynak dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="71acb-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="71acb-109">Microsoft Office 2003 kullanıyorsanız Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk paketini yüklediyseniz Office Open XML biçimindeki belgeleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71acb-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="71acb-110">WordprocessingML belgelerinin şekli</span><span class="sxs-lookup"><span data-stu-id="71acb-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="71acb-111">Anlaşılması gereken ilk şey WordprocessingML belgelerinin şekildir.</span><span class="sxs-lookup"><span data-stu-id="71acb-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="71acb-112">WordprocessingML belgesi, belgenin paragraflarını içeren bir body öğesi (`w:body`) içerir.</span><span class="sxs-lookup"><span data-stu-id="71acb-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="71acb-113">Her paragraf bir veya daha fazla metin çalıştırması (`w:r`adlı) içerir.</span><span class="sxs-lookup"><span data-stu-id="71acb-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="71acb-114">Her metin çalışması bir veya daha fazla metin parçası içerir (`w:t`olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="71acb-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="71acb-115">Aşağıda çok basit bir WordprocessingML belgesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="71acb-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="71acb-116">Bu belge iki paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="71acb-116">This document contains two paragraphs.</span></span> <span data-ttu-id="71acb-117">Her ikisi de tek bir metin çalıştırması içerir ve her metin çalışması tek bir metin parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="71acb-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="71acb-118">XML biçiminde bir WordprocessingML belgesinin içeriğini görmenin en kolay yolu Microsoft Word 'Ü kullanarak bir tane oluşturmak, kaydetmeniz ve ardından XML 'i konsola yazdıran aşağıdaki programı çalıştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="71acb-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="71acb-119">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="71acb-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="71acb-120"><xref:System.IO.Packaging?displayProperty=nameWithType> ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="71acb-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="71acb-121">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="71acb-121">External Resources</span></span>  
 <span data-ttu-id="71acb-122">[Office (2007) Open XML dosya biçimlerine giriş](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="71acb-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>  
  
 <span data-ttu-id="71acb-123">[WordprocessingML 'ye Genel Bakış](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span><span class="sxs-lookup"><span data-stu-id="71acb-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>  
  
 [<span data-ttu-id="71acb-124">Office 2003: XML başvuru şemaları Indirme sayfası</span><span class="sxs-lookup"><span data-stu-id="71acb-124">Office 2003: XML Reference Schemas Download page</span></span>](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="71acb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71acb-125">See also</span></span>

- [<span data-ttu-id="71acb-126">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71acb-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
