---
title: "Şekil WordprocessingML belgeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f29ed78062337c7036ada2405fa610ff1f883feb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Şekil WordprocessingML belgeleri (Visual Basic)
Bu konu WordprocessingML belge XML şeklini tanıtır.  
  
## <a name="microsoft-office-formats"></a>Microsoft Office biçimleri  
 Office Açık XML (Açık XML olarak bilinir) 2007 Microsoft Office sistemi için yerel dosya biçimidir. Açık XML'dir biçimlendirmek XML tabanlı bir Ecma standardı ve şu anda ISO IEC standartları sürecinden. Open XML içinde sözcük işleme dosyaları için biçimlendirme dili WordprocessingML adı verilir. Bu öğretici WordprocessingML kaynak dosyaları örnekler için giriş olarak kullanır.  
  
 Microsoft Office 2003 kullanıyorsanız, Office Açık XML biçiminde yüklediyseniz belgeleri kaydedebilirsiniz Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Şekil WordprocessingML belgeleri  
 Şekil WordprocessingML belgelerin anlamak için ilk şeydir. WordprocessingML belge body öğesi içeriyor (adlı `w:body`), belgenin paragraf içerir. Bir veya daha fazla metin çalışıyor her paragraf içerir (adlı `w:r`). Bir veya daha fazla metin parçaları çalıştırmak her metni içeren (adlı `w:t`).  
  
 Çok basit bir WordprocessingML belge verilmiştir:  
  
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
  
 Bu belge iki paragraf içeriyor. Her ikisi de çalıştıran tek bir metin içermelidir ve tek bir metin parça çalıştırmak her metin içeriyor.  
  
 XML formundaki WordprocessingML belgesinin içeriğini görmek için en kolay yolu bir Microsoft Word kaydedin kullanarak ve ardından XML konsola yazdırır aşağıdaki programı çalıştırın oluşturmaktır.  
  
 Bu örnek WindowsBase derlemesinde sınıfları kullanır. Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.  
  
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
  
## <a name="external-resources"></a>Dış Kaynaklar  
 [Office (2007) açık XML dosya biçimleri](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [WordprocessingML genel bakış](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [Office 2003: XML şemaları başvuru indirme sayfası](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Düzenleme içeriği WordprocessingML belgesinde (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
