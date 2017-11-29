---
title: "Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 40abf687aab985983a574daaa9db799c67b8540e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama
Bir virgülle ayrılmış değer (CSV) dosyası elektronik tablo verileri veya satırları ve sütunları tarafından temsil edilen diğer tablo verileri depolamak için kullanılan bir metin dosyasıdır. Kullanarak <xref:System.String.Split%2A> alanlarını ayırmak için yöntemi sorgulamak ve LINQ kullanarak CSV dosyalarını işlemek çok kolaydır. Aslında, aynı tekniği yapılandırılmış her metin satırının bölümlerini yeniden sıralamak için kullanılabilir; CSV dosyaları için sınırlı değildir.  
  
 Aşağıdaki örnekte, üç sütun Öğrenciler "son adı," temsil varsayalım "ad" ve "Kimlik" Öğrenciler son adlarına göre alfabetik sırada alanlardır. Sorgu ID sütunu öğrencinin ilk ad ve Soyadı birleştiren ikinci bir sütun tarafından izlenen ilk göründüğü yeni bir sıra oluşturur. Satırları ID alanı göre düzenlenir. Sonuçları yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.  
  
### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
1.  Aşağıdaki satırları spreadsheet1.csv adlı bir düz metin dosyasına kopyalayın. Proje klasörünüzdeki dosyayı kaydedin.  
  
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
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Nasıl yapılır: XML CSV dosyalarından oluştur](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
