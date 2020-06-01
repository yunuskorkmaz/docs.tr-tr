---
title: XML dosyasından nesne verilerini okuma (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: e2365d1260d3f6e239f294b2af3399c2fb659575
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241883"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>XML dosyasından nesne verilerini okuma (C#)
Bu örnek, daha önce sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> .  
  
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
"C:\temp\SerializationOverview.xml" dosya adını seri hale getirilen verileri içeren dosyanın adıyla değiştirin. Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [BIR XML dosyasına nesne verileri yazma (C#)](./how-to-write-object-data-to-an-xml-file.md).
  
 Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.  
  
 Yalnızca ortak özellikler ve alanların serisi kaldırılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
- Dosyadaki veriler, seri durumdan çıkarılacak sınıftan verileri temsil etmez.  
  
- Dosya yok ( <xref:System.IO.IOException> ).  
  
## <a name="net-security"></a>.NET güvenliği  
 Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktaki verileri hiçbir zaman serisini kaldırma. Yeniden oluşturulan nesne, yerel bir bilgisayarda, serisi kaldırılan kodun izinleriyle çalışır. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Nesne verilerini bir XML dosyasına yazma (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Serileştirme (C# )](./index.md)
- [C# Programlama Kılavuzu](../../index.md)
