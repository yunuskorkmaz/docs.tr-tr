---
title: 'Nasıl yapılır: (LINQ) sınırlandırılmış bir dosyanın alanlarını yeniden sıralama (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 260f3dff25eb1e9c47a8102822da709bdede9b72
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584433"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Nasıl yapılır: (LINQ) sınırlandırılmış bir dosyanın alanlarını yeniden sıralama (C#)
Bir virgülle ayrılmış değer (CSV) dosyası, genellikle elektronik tablo verilerini veya satırları ve sütunları tarafından temsil edilen diğer tablosal verileri depolamak için kullanılan bir metin dosyasıdır. Kullanarak <xref:System.String.Split%2A> yöntemi alanlarını ayırmak için sorgulama ve LINQ kullanarak CSV dosyalarını işlemek çok kolaydır. Aslında, yapılandırılmış her metin satırının bölümlerini yeniden sıralamak için aynı tekniği kullanılabilir; CSV dosyaları için sınırlı değildir.  
  
 Aşağıdaki örnekte, üç sütun öğrencilerinin "Soyadı" temsil ettiğini varsayar "ad" ve "Kimliği" Öğrencilerinin son adlarına göre alfabetik sırada alanlardır. Sorgu, kimlik sütunu öğrencinin ad ve Soyadı birleştiren ikinci sütuna göre ve ardından ilk göründüğü yeni bir sıra üretir. Satır Kimliği alanı göre sıralanır. Sonuçları yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.  
  
### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
1. Aşağıdaki satırları spreadsheet1.csv adlı bir düz metin dosyasına kopyalayın. Dosyayı proje klasörünüze kaydedin.  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a>Örnek  
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
Oluşturma bir C# konsol uygulama projesi ile `using` System.Linq ve System.IO ad alanları için yönergeleri.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Nasıl yapılır: CSV dosyalarından XML oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
