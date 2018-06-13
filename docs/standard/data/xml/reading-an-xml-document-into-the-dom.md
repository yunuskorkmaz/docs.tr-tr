---
title: Bir XML belgesi DOM okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad649e61f4f006103d38a998eece174a07889828
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569726"
---
# <a name="reading-an-xml-document-into-the-dom"></a>Bir XML belgesi DOM okuma
Farklı biçimlerden belleğe XML bilgileri okuyun. Bir dize, akışı, URL, metin okuyucu veya türetilmiş bir sınıf okunabilir <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Yöntemi belge belleğe getirir ve her biri farklı biçimlerde verileri almak için kullanılabilen yöntemler aşırı yüklü. Ayrıca bir <xref:System.Xml.XmlDocument.LoadXml%2A> bir dizeden XML okur yöntemi.  
  
 Farklı <xref:System.Xml.XmlDocument.Load%2A> yöntemleri etkileyen XML belge nesne modeli (DOM) yüklendiğinde hangi düğümlerin oluşturulur. Aşağıdaki tabloda bazı arasındaki farklar listelenmektedir <xref:System.Xml.XmlDocument.Load%2A> yöntemleri ve bunları adres Konular.  
  
|Konu|Konu|  
|-------------|-----------|  
|Beyaz alan düğümlerinin oluşturma|DOM yükleme için kullanılan nesne boşluk ve DOM içinde oluşturulan önemli boşluk düğümleri üzerinde bir etkisi Daha fazla bilgi için bkz: [boşluk ve önemli boşluk DOM yüklenirken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Belirli bir düğümünden başlayan XML yüklenirken veya tüm XML belgesi yüklenirken|Kullanarak <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> yöntemi veri yüklenebilir belirli bir düğümden DOM Daha fazla bilgi için bkz: [bir okuyucu yük verileri](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|XML olarak doğrulama yüklendi|Yüklendiği gibi DOM yüklenen XML veriler doğrulanamıyor. Bu bir doğrulama kullanılarak gerçekleştirilir <xref:System.Xml.XmlReader>. Yüklendiği gibi XML doğrulama hakkında daha fazla bilgi için bkz: [XML belgesi DOM içinde doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Aşağıdaki örnek ile yüklenen XML gösterir <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemi ve daha sonra bir metin dosyasına kaydedilen verileri adlı `data.xml`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
