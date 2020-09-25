---
title: Ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)
description: C# ' de LINQ içindeki bir. csv dosyasındaki alanları yeniden düzenleme hakkında bilgi edinin. Örnek sütun ve sütunları bir sütun değerine göre sıralar.
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 674e6a62112e17107eff690d7656f52488cd08c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203962"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)

Virgülle ayrılmış değer (CSV) dosyası, elektronik tablo verilerini veya satırlar ve sütunlar tarafından temsil edilen diğer tablo verilerini depolamak için genellikle kullanılan bir metin dosyasıdır. <xref:System.String.Split%2A>Alanları ayırmak için yöntemini kullanarak, LINQ kullanarak CSV dosyalarını sorgulamak ve işlemek çok kolaydır. Aslında, yapılandırılmış herhangi bir metin satırının parçalarını yeniden sıralamak için aynı teknik de kullanılabilir; CSV dosyalarıyla sınırlı değildir.  
  
 Aşağıdaki örnekte, üç sütunun öğrencileri ' "soyadı," "First Name" ve "ID" temsil ettiğini varsayın. Alanlar, öğrencilerin son adlarına göre alfabetik sıralardır. Sorgu önce KIMLIK sütununun ilk göründüğü yeni bir dizi oluşturur, ardından öğrencinin adı ve soyadı birleştiren ikinci bir sütun gelir. Satırlar KIMLIK alanına göre yeniden sıralanabilir. Sonuçlar yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.  
  
### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
1. Aşağıdaki satırları spreadsheet1.csv adında bir düz metin dosyasına kopyalayın. Dosyayı proje klasörünüze kaydedin.  
  
    ```csv  
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

`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
- [LINQ ve dosya dizinleri (C#)](./linq-and-file-directories.md)
- [CSV dosyalarından XML oluşturma (C#)](../../../../standard/linq/generate-xml-csv-files.md)
