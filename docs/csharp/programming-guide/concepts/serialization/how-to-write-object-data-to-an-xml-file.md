---
title: "Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f43075c0b4d04ff935e7a29ed270b348209d17b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma
Bu örnek, bir XML dosyası kullanarak bir sınıftan nesne Yazar <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
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
 Sınıf parametresiz ortak bir oluşturucuya sahip olmalıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Serileştirilen sınıfı genel, parametresiz bir oluşturucu yok.  
  
-   Dosya var ve salt okunurdur (<xref:System.IO.IOException>).  
  
-   Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Disk dolu olduğundan (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmak gerekirse, bu uygulamanın ihtiyacı `Create` klasörü için erişim. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişimi, daha düşük ayrıcalık. Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca izni için daha güvenli olan `Read` tek bir dosyaya erişim yerine `Create` bir klasör için erişim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamWriter>  
 [Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Seri hale getirme (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)
