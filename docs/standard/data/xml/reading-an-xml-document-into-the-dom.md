---
title: DOM’da XML Belgesi Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 2e61a9ed1a1ccaa2f9f1543efa1d33c3fcf00061
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130841"
---
# <a name="reading-an-xml-document-into-the-dom"></a>DOM’da XML Belgesi Okuma
XML bilgileri farklı biçimlerden belleğe okundu. Bir dize, akış, URL, metin okuyucu veya öğesinden türetilmiş bir sınıftan okunabilir <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Yöntemi, belgeyi belleğe getirir ve farklı biçimlerden her birinden veri almak için kullanılabilir yöntemler daha fazla bulunabilir. Ayrıca, bir dizeden <xref:System.Xml.XmlDocument.LoadXml%2A> XML okuyan bir yöntem de vardır.  
  
 Farklı <xref:System.Xml.XmlDocument.Load%2A> Yöntemler, XML belge nesne MODELI (DOM) yüklendiğinde hangi düğümlerin oluşturulduğunu etkiler. Aşağıdaki tabloda, <xref:System.Xml.XmlDocument.Load%2A> bunları ele alan bazı yöntemler ve konular arasındaki farklılıklar listelenmiştir.  
  
|Özne|Konu başlığı|  
|-------------|-----------|  
|Boşluk düğümleri oluşturma|DOM 'ı yüklemek için kullanılan nesnenin, DOM 'da oluşturulan, boşluk ve önemli boşluk düğümleri üzerinde bir etkisi vardır. Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Belirli bir düğümden başlayarak XML yükleme veya tüm XML belgesi yükleme|Yöntem verilerinin <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> kullanılması, belirli BIR düğümden Dom 'a yüklenebilir. Daha fazla bilgi için bkz. [okuyucudan veri yükleme](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|XML yüklendiği için doğrulanıyor|DOM 'a yüklenen XML verileri, yüklendiği için doğrulanabilir. Bu, doğrulama <xref:System.Xml.XmlReader>kullanılarak gerçekleştirilir. XML 'nin yüklendiği şekilde doğrulanması hakkında daha fazla bilgi için bkz. [Dom 'da BIR XML belgesini doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Aşağıdaki örnek, <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemi ile YÜKLENMEKTE olan XML ve daha sonra adlı `data.xml`bir metin dosyasına kaydedilen verileri gösterir.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
