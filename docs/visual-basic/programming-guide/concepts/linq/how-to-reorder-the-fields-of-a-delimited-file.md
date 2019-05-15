---
title: 'Nasıl yapılır: (LINQ) (Visual Basic) sınırlandırılmış bir dosyanın alanlarını yeniden sıralama'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 25f860109275bdee1b980c68e71c2c65d44756a4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593104"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="07f22-102">Nasıl yapılır: (LINQ) (Visual Basic) sınırlandırılmış bir dosyanın alanlarını yeniden sıralama</span><span class="sxs-lookup"><span data-stu-id="07f22-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="07f22-103">Bir virgülle ayrılmış değer (CSV) dosyası, genellikle elektronik tablo verilerini veya satırları ve sütunları tarafından temsil edilen diğer tablosal verileri depolamak için kullanılan bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="07f22-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="07f22-104">Kullanarak <xref:System.String.Split%2A> yöntemi alanlarını ayırmak için sorgulama ve LINQ kullanarak CSV dosyalarını işlemek çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="07f22-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="07f22-105">Aslında, yapılandırılmış her metin satırının bölümlerini yeniden sıralamak için aynı tekniği kullanılabilir; CSV dosyaları için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="07f22-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="07f22-106">Aşağıdaki örnekte, üç sütun öğrencilerinin "Soyadı" temsil ettiğini varsayar "ad" ve "Kimliği"</span><span class="sxs-lookup"><span data-stu-id="07f22-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="07f22-107">Öğrencilerinin son adlarına göre alfabetik sırada alanlardır.</span><span class="sxs-lookup"><span data-stu-id="07f22-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="07f22-108">Sorgu, kimlik sütunu öğrencinin ad ve Soyadı birleştiren ikinci sütuna göre ve ardından ilk göründüğü yeni bir sıra üretir.</span><span class="sxs-lookup"><span data-stu-id="07f22-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="07f22-109">Satır Kimliği alanı göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="07f22-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="07f22-110">Sonuçları yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="07f22-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="07f22-111">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="07f22-111">To create the data file</span></span>  
  
1. <span data-ttu-id="07f22-112">Aşağıdaki satırları spreadsheet1.csv adlı bir düz metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="07f22-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="07f22-113">Dosyayı proje klasörünüze kaydedin.</span><span class="sxs-lookup"><span data-stu-id="07f22-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="07f22-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="07f22-114">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07f22-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07f22-115">See also</span></span>

- [<span data-ttu-id="07f22-116">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07f22-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="07f22-117">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07f22-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="07f22-118">Nasıl yapılır: CSV dosyalarından XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="07f22-118">How to: Generate XML from CSV Files</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
