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
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="29393-102">Nasıl yapılır: sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama</span><span class="sxs-lookup"><span data-stu-id="29393-102">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>
<span data-ttu-id="29393-103">Bir virgülle ayrılmış değer (CSV) dosyası, genellikle elektronik tablo verilerini veya satırları ve sütunları tarafından temsil edilen diğer tablosal verileri depolamak için kullanılan bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="29393-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="29393-104">Kullanarak <xref:System.String.Split%2A> yöntemi alanlarını ayırmak için sorgulama ve LINQ kullanarak CSV dosyalarını işlemek çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="29393-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="29393-105">Aslında, yapılandırılmış her metin satırının bölümlerini yeniden sıralamak için aynı tekniği kullanılabilir; CSV dosyaları için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="29393-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="29393-106">Aşağıdaki örnekte, üç sütun öğrencilerinin "Soyadı" temsil ettiğini varsayar "ad" ve "Kimliği"</span><span class="sxs-lookup"><span data-stu-id="29393-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="29393-107">Öğrencilerinin son adlarına göre alfabetik sırada alanlardır.</span><span class="sxs-lookup"><span data-stu-id="29393-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="29393-108">Sorgu, kimlik sütunu öğrencinin ad ve Soyadı birleştiren ikinci sütuna göre ve ardından ilk göründüğü yeni bir sıra üretir.</span><span class="sxs-lookup"><span data-stu-id="29393-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="29393-109">Satır Kimliği alanı göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="29393-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="29393-110">Sonuçları yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="29393-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="29393-111">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="29393-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="29393-112">Aşağıdaki satırları spreadsheet1.csv adlı bir düz metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="29393-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="29393-113">Dosyayı proje klasörünüze kaydedin.</span><span class="sxs-lookup"><span data-stu-id="29393-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="29393-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="29393-114">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="29393-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="29393-115">Compiling the Code</span></span>  
 <span data-ttu-id="29393-116">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="29393-116">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29393-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29393-117">See Also</span></span>

- [<span data-ttu-id="29393-118">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="29393-118">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [<span data-ttu-id="29393-119">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="29393-119">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [<span data-ttu-id="29393-120">Nasıl yapılır: XML, CSV dosyalarından (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="29393-120">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
