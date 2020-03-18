---
title: XML dosyasından nesne verileri nasıl okunur (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167824"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>XML dosyasından nesne verileri nasıl okunur (C#)
Bu örnek, <xref:System.Xml.Serialization.XmlSerializer> sınıfı kullanarak daha önce bir XML dosyasına yazılmış nesne verilerini okur.  
  
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
"c:\temp\SerializationOverview.xml" dosya adını serileştirilmiş verileri içeren dosyanın adı ile değiştirin. Verileri serileştirme hakkında daha fazla bilgi için, [nesne verilerinin XML dosyasına (C#) nasıl yazılması](./how-to-write-object-data-to-an-xml-file.md)nabakını görün.
  
 Sınıfın parametreleri olmayan bir ortak oluşturucusu olmalıdır.  
  
 Yalnızca ortak özellikler ve alanlar deserialized vardır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Serihale edilen sınıfın ortak, parametresiz bir oluşturucusu yoktur.  
  
- Dosyadaki veriler, seri olmaktan çıkarılacak sınıftaki verileri temsil etmez.  
  
- Dosya yok (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktan gelen verileri asla deserialize edin. Yeniden oluşturulan nesne, onu deserialize eden kodun izinleriyle yerel bir bilgisayarda çalışır. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [Bir XML dosyasına nesne verileri yazma (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Serileştirme (C# )](./index.md)
- [C# Programlama Kılavuzu](../../index.md)
