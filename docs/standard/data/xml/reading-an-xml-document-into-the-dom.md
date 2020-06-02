---
title: DOM’da XML Belgesi Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 02338d72f51d3a7507c0dfa030383399b9e213f6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282408"
---
# <a name="reading-an-xml-document-into-the-dom"></a>DOM’da XML Belgesi Okuma
XML bilgileri farklı biçimlerden belleğe okundu. Bir dize, akış, URL, metin okuyucu veya öğesinden türetilmiş bir sınıftan okunabilir <xref:System.Xml.XmlReader> .  
  
 <xref:System.Xml.XmlDocument.Load%2A>Yöntemi, belgeyi belleğe getirir ve farklı biçimlerden her birinden veri almak için kullanılabilir yöntemler daha fazla bulunabilir. Ayrıca, <xref:System.Xml.XmlDocument.LoadXml%2A> bir DIZEDEN XML okuyan bir yöntem de vardır.  
  
 Farklı <xref:System.Xml.XmlDocument.Load%2A> Yöntemler, XML belge nesne modeli (DOM) yüklendiğinde hangi düğümlerin oluşturulduğunu etkiler. Aşağıdaki tabloda, <xref:System.Xml.XmlDocument.Load%2A> bunları ele alan bazı yöntemler ve konular arasındaki farklılıklar listelenmiştir.  
  
|Özne|Konu başlığı|  
|-------------|-----------|  
|Boşluk düğümleri oluşturma|DOM 'ı yüklemek için kullanılan nesnenin, DOM 'da oluşturulan, boşluk ve önemli boşluk düğümleri üzerinde bir etkisi vardır. Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Belirli bir düğümden başlayarak XML yükleme veya tüm XML belgesi yükleme|<xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType>Yöntem verilerinin kullanılması, belirli bir DÜĞÜMDEN Dom 'a yüklenebilir. Daha fazla bilgi için bkz. [okuyucudan veri yükleme](load-data-from-a-reader.md).|  
|XML yüklendiği için doğrulanıyor|DOM 'a yüklenen XML verileri, yüklendiği için doğrulanabilir. Bu, doğrulama kullanılarak gerçekleştirilir <xref:System.Xml.XmlReader> . XML 'nin yüklendiği şekilde doğrulanması hakkında daha fazla bilgi için bkz. [Dom 'da BIR XML belgesini doğrulama](validating-an-xml-document-in-the-dom.md).|  
  
 Aşağıdaki örnek, yöntemi ile yüklenmekte olan XML <xref:System.Xml.XmlDocument.LoadXml%2A> ve daha sonra adlı bir metin dosyasına kaydedilen verileri gösterir `data.xml` .  
  
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

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
