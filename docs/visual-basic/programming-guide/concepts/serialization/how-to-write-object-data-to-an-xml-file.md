---
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 9608a48cb8b3fac1c71affa7a0a17e9789f94b18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413160"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)
Bu örnek, sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar <xref:System.Xml.Serialization.XmlSerializer> .  
  
## <a name="example"></a>Örnek  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a>Kodu derle  
 Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
- Dosya var ve salt okunurdur ( <xref:System.IO.IOException> ).  
  
- Yol çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
- Disk dolu ( <xref:System.IO.IOException> ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasöre erişmesi gerekir. Dosya zaten mevcutsa, uygulamanın yalnızca daha `Write` az bir ayrıcalığa erişmesi gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve `Read` `Create` bir klasör için erişim yerine yalnızca tek bir dosyaya erişim izni verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)](how-to-read-object-data-from-an-xml-file.md)
- [Serileştirme (Visual Basic)](index.md)
