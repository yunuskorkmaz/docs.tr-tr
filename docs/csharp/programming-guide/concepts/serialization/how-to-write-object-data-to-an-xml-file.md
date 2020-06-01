---
title: Nesne verilerini bir XML dosyasına yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 6f18ae194d2ed70f633665a29772622319ea9493
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242000"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Nesne verilerini bir XML dosyasına yazma (C#)
Bu örnek, sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar <xref:System.Xml.Serialization.XmlSerializer> .  
  
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
 Seri hale getirilen sınıfın parametre içermeyen bir ortak Oluşturucusu olmalıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.  
  
- Dosya var ve salt okunurdur ( <xref:System.IO.IOException> ).  
  
- Yol çok uzun ( <xref:System.IO.PathTooLongException> ).  
  
- Disk dolu ( <xref:System.IO.IOException> ).  
  
## <a name="net-security"></a>.NET güvenliği  
 Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasöre erişmesi gerekir. Dosya zaten mevcutsa, uygulamanın yalnızca daha `Write` az bir ayrıcalığa erişmesi gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve `Read` `Create` bir klasör için erişim yerine yalnızca tek bir dosyaya erişim izni verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- [XML dosyasından nesne verilerini okuma (C#)](./how-to-read-object-data-from-an-xml-file.md)
- [Serileştirme (C# )](./index.md)
