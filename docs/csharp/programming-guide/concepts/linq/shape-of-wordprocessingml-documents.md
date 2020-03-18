---
title: WordprocessingML Belgelerin şekli (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76732678"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>WordprocessingML Belgelerin şekli (C#)
Bu konu, WordprocessingML belgesinin XML şeklini tanır.  
  
## <a name="microsoft-office-formats"></a>Microsoft Office Biçimleri  
 2007 Microsoft Office sisteminin yerel dosya biçimi Office Open XML 'dir (genellikle Açık XML olarak adlandırılır). Open XML, Bir Ecma standardı olan ve şu anda ISO-IEC standart sürecinden geçmekte olan XML tabanlı bir biçimdir. Açık XML içindeki sözcük işleme dosyalarının biçimlendirme dili WordprocessingML olarak adlandırılır. Bu öğretici, örnekler için giriş olarak WordprocessingML kaynak dosyalarını kullanır.  
  
 Microsoft Office 2003 kullanıyorsanız, Word, Excel ve PowerPoint 2007 Dosya Biçimleri için Microsoft Office Uyumluluk Paketi yüklediyseniz Belgeleri Office Open XML biçiminde kaydedebilirsiniz.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>WordprocessingML Belgelerin Şekli  
 Anlamak için ilk şey WordprocessingML belgelerin şeklidir. WordprocessingML belgesi, belgenin paragraflarını içeren bir gövde öğesi (adlandırılmış) `w:body`içerir. Her paragraf bir veya daha `w:r`fazla metin çalışır (adlandırılmış) içerir. Her metin çalıştırıcı bir veya `w:t`daha fazla metin parçaları (adlandırılmış) içerir.  
  
 Aşağıdaki çok basit bir WordprocessingML belgedir:  
  
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
  
 Bu belge iki paragraf içerir. Her ikisi de tek bir metin çalışması içerir ve her metin çalışması tek bir metin parçası içerir.  
  
 Bir WordprocessingML belgesinin içeriğini XML formunda görmenin en kolay yolu, Microsoft Word'ü kullanarak bir belge oluşturmak, kaydetmek ve ardından XML'yi konsola yazdıran aşağıdaki programı çalıştırmaktır.  
  
 Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.  
  
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
  
## <a name="external-resources"></a>Dış kaynaklar

- [Office Tanıtımı (2007) Açık XML Dosya Biçimleri](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [WordprocessingML'e Genel Bakış](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [Bir WordProcessingML Dosyaanatomisi](http://officeopenxml.com/anatomyofOOXML.php)
- [WordprocessingML'e Giriş](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)](./shape-of-wordprocessingml-documents.md)
