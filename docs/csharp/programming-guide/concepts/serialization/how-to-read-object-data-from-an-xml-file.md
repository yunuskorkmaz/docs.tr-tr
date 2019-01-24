---
title: 'Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 33e4395c2be421385948d256a989d06ac215c9c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583492"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma (C#)
Bu örnek daha önce bir XML dosyası kullanmayı yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
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
 Dosya adı "c:\temp\SerializationOverview.xml" seri hale getirilmiş veri içeren dosyanın adıyla değiştirin. Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.  
  
 Yalnızca ortak özellikler ve alanları seri.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
-   Dosyasındaki verilerin veri seri durumdan sınıftan temsil etmiyor.  
  
-   Dosya yok (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan gelen verileri seri durumdan. Yeniden oluşturulan nesne, seri durumdan kodun izinlere sahip bir yerel bilgisayarda çalıştırır. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [Seri hale getirme (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
