---
title: DOM'da XML belgesi okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9031f5df0d0f48dc2844cdfd0654ee4ab876cc22
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842534"
---
# <a name="reading-an-xml-document-into-the-dom"></a>DOM'da XML belgesi okuma
Farklı biçimler belleğe XML bilgileri okuyun. Bir dize, akış, URL, metin okuyucuyu ya da türetilen bir sınıf okunabilir <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Yöntemi her farklı biçimlerde veri almak için kullanılabilen yöntemler aşırı yüklü ve belleğe belge getirir. Ayrıca bir <xref:System.Xml.XmlDocument.LoadXml%2A> XML bir dizeden okur yöntemi.  
  
 Farklı <xref:System.Xml.XmlDocument.Load%2A> yöntemleri etkileyen XML belge nesne modeli (DOM) yüklendiğinde hangi düğümleri oluşturulur. Aşağıdaki tabloda bazı arasındaki farklar listelenmektedir <xref:System.Xml.XmlDocument.Load%2A> yöntemleri ve onları adreslemek konuları.  
  
|Konu|Konu|  
|-------------|-----------|  
|Boşluk düğümleri oluşturma|DOM yükleme için kullanılan nesne boşluk ve DOM oluşturulan önemli boşluk düğümleri üzerinde bir etkisi Daha fazla bilgi için [boşluk ve önemli boşluk DOM yüklerken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Belirli bir düğümünden başlayan XML yüklenirken veya tüm XML belgesi yüklenirken|Kullanarak <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> yöntemi veri yüklenebilir belirli bir düğüm DOM'a Daha fazla bilgi için [bir okuyucudan veri yükleme](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|XML olarak doğrulama yüklendi|Yüklü olduğu gibi DOM'a XML verileri doğrulanamıyor. Bu bir doğrulama kullanılarak gerçekleştirilir <xref:System.Xml.XmlReader>. Yüklü olduğu gibi XML doğrulama hakkında daha fazla bilgi için bkz. [doğrulama bir XML belgesi DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Aşağıdaki örnek, XML ile yüklenen gösterir <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemi ve daha sonra bir metin dosyasına kaydedilmiş veri adlı `data.xml`.  
  
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
