---
title: "Nasıl yapılır: nesne verilerini bir XML dosyasından (Visual Basic) okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Nasıl yapılır: nesne verilerini bir XML dosyasından (Visual Basic) okuma
Bu örnek daha önce bir XML dosyası kullanmaya yazıldı nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
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
 Dosya adı "c:\temp\SerializationOverview.xml" serileştirilmiş verilerini içeren dosyanın adı ile değiştirin. Verileri seri hale getirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesne verilerini bir XML dosyasına (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Sınıf parametresiz ortak bir oluşturucuya sahip olmalıdır.  
  
 Yalnızca genel özellikleri ve alanları serisi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Serileştirilen sınıfı genel, parametresiz bir oluşturucu yok.  
  
-   Veri dosyasındaki verileri seri durumdan çıkarılacak sınıfından temsil etmiyor.  
  
-   Dosya yok (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan veri serisi. Yeniden oluşturulan nesne, seri durumdan kod izinleriyle yerel bir bilgisayarda çalıştırır. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamWriter>  
 [Nasıl yapılır: nesne verilerini bir XML dosyası (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [Seri hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
