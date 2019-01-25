---
title: 'Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: a7784566cba7b9cf85914a410b78240856879ba8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715835"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma
Bu örnek, bir XML dosyası kullanmayı öğesinden bir sınıf nesnesi Yazar <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
-   Dosya var ve salt okunur (<xref:System.IO.IOException>).  
  
-   Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Disk dolu (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulamayı gerekli `Create` klasörü için erişim. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişim, daha az ayrıcalıkla. Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` tek bir dosyaya erişimi yerine `Create` erişim için bir klasör.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IO.StreamWriter>
- [Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Seri hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
