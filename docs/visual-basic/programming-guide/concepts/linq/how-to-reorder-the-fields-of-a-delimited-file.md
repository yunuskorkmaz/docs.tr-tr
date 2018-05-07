---
title: 'Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (Visual Basic) alanlarını yeniden sıralama'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 4bef55c35311672ab3f28c2ce04a64e1cd21c170
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (Visual Basic) alanlarını yeniden sıralama
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
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Nasıl yapılır: CSV Dosyalarından XML Oluşturma](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
