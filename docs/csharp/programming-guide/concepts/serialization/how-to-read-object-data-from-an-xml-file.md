---
title: "Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a3389de2f3272a546a7380ef386f5d88666e6d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma
Bu örnek daha önce bir XML dosyası kullanmaya yazıldı nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
## <a name="example"></a>Örnek  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Dosya adı "c:\temp\SerializationOverview.xml" serileştirilmiş verilerini içeren dosyanın adı ile değiştirin. Verileri seri hale getirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
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
 [Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [Seri hale getirme (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)
