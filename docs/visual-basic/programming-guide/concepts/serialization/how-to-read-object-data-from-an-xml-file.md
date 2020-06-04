---
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasından Okuma'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: 7097ec146987aea7855da40dd30f9cd3c17d8ce4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413173"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)
Bu örnek, daha önce sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> .  
  
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
  
## <a name="compile-the-code"></a>Kodu derle  
 "C:\temp\SerializationOverview.xml" dosya adını seri hale getirilen verileri içeren dosyanın adıyla değiştirin. Verileri serileştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne verilerini BIR XML dosyasına yazma (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).  
  
 Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.  
  
 Yalnızca ortak özellikler ve alanların serisi kaldırılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
- Dosyadaki veriler, seri durumdan çıkarılacak sınıftan verileri temsil etmez.  
  
- Dosya yok ( <xref:System.IO.IOException> ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktaki verileri hiçbir zaman serisini kaldırma. Yeniden oluşturulan nesne, yerel bir bilgisayarda, serisi kaldırılan kodun izinleriyle çalışır. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)
- [Serileştirme (Visual Basic)](index.md)
- [Visual Basic Programlama Kılavuzu](../../index.md)
