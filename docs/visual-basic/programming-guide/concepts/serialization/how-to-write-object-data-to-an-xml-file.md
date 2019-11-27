---
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: b2181a74c83782cf4737b2a94fc5fb08fee28a10
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345451"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)
Bu örnek, <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
- Dosya var ve salt okunurdur (<xref:System.IO.IOException>).  
  
- Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Disk dolu (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için `Create` erişimi olması gerekir. Dosya zaten mevcutsa, uygulamanın daha az bir ayrıcalığa yalnızca `Write` erişimi olması gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve bir klasör için `Create` erişimi yerine yalnızca tek bir dosyaya `Read` erişim izni verilmesi daha güvenlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serileştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
