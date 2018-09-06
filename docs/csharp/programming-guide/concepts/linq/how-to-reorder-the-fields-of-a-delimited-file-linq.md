---
title: 'Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 24d1bf9825e00d0764846a0ae83ae73cd0ea03e1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869162"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama
Bir virgülle ayrılmış değer (CSV) dosyası, genellikle elektronik tablo verilerini veya satırları ve sütunları tarafından temsil edilen diğer tablosal verileri depolamak için kullanılan bir metin dosyasıdır. Kullanarak <xref:System.String.Split%2A> yöntemi alanlarını ayırmak için sorgulama ve LINQ kullanarak CSV dosyalarını işlemek çok kolaydır. Aslında, yapılandırılmış her metin satırının bölümlerini yeniden sıralamak için aynı tekniği kullanılabilir; CSV dosyaları için sınırlı değildir.  
  
 Aşağıdaki örnekte, üç sütun öğrencilerinin "Soyadı" temsil ettiğini varsayar "ad" ve "Kimliği" Öğrencilerinin son adlarına göre alfabetik sırada alanlardır. Sorgu, kimlik sütunu öğrencinin ad ve Soyadı birleştiren ikinci sütuna göre ve ardından ilk göründüğü yeni bir sıra üretir. Satır Kimliği alanı göre sıralanır. Sonuçları yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.  
  
### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
1.  Aşağıdaki satırları spreadsheet1.csv adlı bir düz metin dosyasına kopyalayın. Dosyayı proje klasörünüze kaydedin.  
  
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
 .NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [Nasıl yapılır: XML, CSV dosyalarından (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
