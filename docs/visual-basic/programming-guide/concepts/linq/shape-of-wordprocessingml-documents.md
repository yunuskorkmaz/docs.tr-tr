---
title: WordprocessingML Belgelerinin Şekli
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 9dd858e28c010d901c2c5fdfb477fe2c6975dbd4
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76315856"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>WordprocessingML belgelerinin şekli (Visual Basic)
Bu konu, bir WordprocessingML belgesinin XML şeklini tanıtır.  
  
## <a name="microsoft-office-formats"></a>Microsoft Office biçimleri  
 2007 Microsoft Office sistemi için yerel dosya biçimi Office Open XML 'dir (genellikle Open XML olarak adlandırılır). Open XML, bir ECMA Standard ve şu anda ISO-ıEC standartları sürecinden geçen XML tabanlı bir biçimdir. Open XML içindeki sözcük işleme dosyalarının biçimlendirme dili WordprocessingML olarak adlandırılır. Bu öğretici, örnekler için giriş olarak WordprocessingML kaynak dosyalarını kullanır.  
  
 Microsoft Office 2003 kullanıyorsanız Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk paketini yüklediyseniz Office Open XML biçimindeki belgeleri kaydedebilirsiniz.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>WordprocessingML belgelerinin şekli  
 Anlaşılması gereken ilk şey WordprocessingML belgelerinin şekildir. WordprocessingML belgesi, belgenin paragraflarını içeren bir body öğesi (`w:body`) içerir. Her paragraf bir veya daha fazla metin çalıştırması (`w:r`adlı) içerir. Her metin çalışması bir veya daha fazla metin parçası içerir (`w:t`olarak adlandırılır).  
  
 Aşağıda çok basit bir WordprocessingML belgesi verilmiştir:  
  
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
  
 Bu belge iki paragraf içerir. Her ikisi de tek bir metin çalıştırması içerir ve her metin çalışması tek bir metin parçası içerir.  
  
 XML biçiminde bir WordprocessingML belgesinin içeriğini görmenin en kolay yolu Microsoft Word 'Ü kullanarak bir tane oluşturmak, kaydetmeniz ve ardından XML 'i konsola yazdıran aşağıdaki programı çalıştırmalıdır.  
  
 Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanındaki türleri kullanır.  
  
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
  
## <a name="external-resources"></a>Dış kaynaklar

- [Office (2007) Open XML dosya biçimlerine giriş](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))
- [WordprocessingML 'ye Genel Bakış](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
