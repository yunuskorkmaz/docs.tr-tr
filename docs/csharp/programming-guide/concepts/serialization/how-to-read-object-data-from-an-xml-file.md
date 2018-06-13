---
title: 'Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 59110a5bd0fe738239c0ca8b177a8c775db99ccf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336160"
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
 [Serileştirme (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
