---
title: 'Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: b1e9033d7aba8b4f423f29cd4fb4f7efbbe17a29
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624356"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)
Bu örnek daha önce bir XML dosyası kullanmayı yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
## <a name="example"></a>Örnek  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Dosya adı "c:\temp\SerializationOverview.xml" seri hale getirilmiş veri içeren dosyanın adıyla değiştirin. Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.  
  
 Yalnızca ortak özellikler ve alanları seri.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
- Dosyasındaki verilerin veri seri durumdan sınıftan temsil etmiyor.  
  
- Dosya yok (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan gelen verileri seri durumdan. Yeniden oluşturulan nesne, seri durumdan kodun izinlere sahip bir yerel bilgisayarda çalıştırır. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [Seri hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
