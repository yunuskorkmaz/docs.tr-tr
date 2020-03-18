---
title: Bir XML dosyasına nesne verileri yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: f7ffb47a22d3cd94cd7cb6f702b64180a8790eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167524"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Bir XML dosyasına nesne verileri yazma (C#)
Bu örnek, sınıfı kullanarak nesneyi bir sınıftan xml dosyasına <xref:System.Xml.Serialization.XmlSerializer> yazar.  
  
## <a name="example"></a>Örnek  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Serihale alınan sınıfın parametreleri olmayan bir ortak oluşturucusu olmalıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Serihale edilen sınıfın ortak, parametresiz bir oluşturucusu yoktur.  
  
- Dosya var ve salt okunur<xref:System.IO.IOException>( ).  
  
- Yol çok uzun<xref:System.IO.PathTooLongException>( ).  
  
- Disk dolu (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasöre erişmesi gerekir. `Create` Dosya zaten varsa, uygulamanın `Write` yalnızca daha az bir ayrıcalıkla erişmesi gerekir. Mümkün olduğunda, dosyayı dağıtım sırasında oluşturmak ve bir `Read` klasöre erişmek yerine `Create` yalnızca tek bir dosyaya erişim vermek daha güvenlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [XML dosyasından nesne verileri nasıl okunur (C#)](./how-to-read-object-data-from-an-xml-file.md)
- [Serileştirme (C# )](./index.md)
