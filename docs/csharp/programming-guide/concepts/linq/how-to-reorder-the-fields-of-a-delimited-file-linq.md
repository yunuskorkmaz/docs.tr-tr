---
title: Sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 6bc502ff12a908edf43f9ff7f5f63f98c3ff29c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347649"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama
Virgülle ayrılmış değer (CSV) dosyası, genellikle elektronik tablo verilerini veya satır lar ve sütunlarla temsil edilen diğer tabloverilerini depolamak için kullanılan bir metin dosyasıdır. Alanları ayırmak <xref:System.String.Split%2A> için yöntemi kullanarak, LINQ kullanarak CSV dosyalarını sorgulamak ve işlemek çok kolaydır. Aslında, aynı teknik metin herhangi bir yapılandırılmış satırın parçalarını yeniden sipariş etmek için kullanılabilir; CSV dosyaları ile sınırlı değildir.  
  
 Aşağıdaki örnekte, üç sütunun öğrencilerin "soyadı", "adı" ve "Kimliği" temsil ettiğini varsayalım. Alanlar, öğrencilerin soyadlarına göre alfabetik sıraya göre sırayla yapılır. Sorgu, kimlik sütununun önce göründüğü, ardından öğrencinin adı ve soyadını birleştiren ikinci bir sütunun bulunduğu yeni bir sıra üretir. Satırlar kimlik alanına göre yeniden sıralanır. Sonuçlar yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.  
  
### <a name="to-create-the-data-file"></a>Veri dosyasını oluşturmak için  
  
1. Aşağıdaki satırları, elektronik tablo1.csv olarak adlandırılan düz bir metin dosyasına kopyalayın. Dosyayı proje klasörünüze kaydedin.  
  
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
System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dizeleri (C#)](./linq-and-strings.md)
- [LINQ ve Dosya Dizinleri (C#)](./linq-and-file-directories.md)
- [CSV dosyalarından XML nasıl üretilir (C#)](./how-to-generate-xml-from-csv-files.md)
