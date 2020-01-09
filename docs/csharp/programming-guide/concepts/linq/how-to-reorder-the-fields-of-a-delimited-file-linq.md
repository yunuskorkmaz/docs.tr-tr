---
title: Ayrılmış bir dosyanın (LINQ) alanlarını yeniden sıralama (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 6bc502ff12a908edf43f9ff7f5f63f98c3ff29c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347649"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="f2e50-102">Ayrılmış bir dosyanın (LINQ) alanlarını yeniden sıralama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f2e50-102">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="f2e50-103">Virgülle ayrılmış değer (CSV) dosyası, elektronik tablo verilerini veya satırlar ve sütunlar tarafından temsil edilen diğer tablo verilerini depolamak için genellikle kullanılan bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2e50-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="f2e50-104">Alanları ayırmak için <xref:System.String.Split%2A> yöntemini kullanarak, LINQ kullanarak CSV dosyalarını sorgulamak ve işlemek çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="f2e50-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="f2e50-105">Aslında, yapılandırılmış herhangi bir metin satırının parçalarını yeniden sıralamak için aynı teknik de kullanılabilir; CSV dosyalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f2e50-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="f2e50-106">Aşağıdaki örnekte, üç sütunun öğrencileri ' "soyadı," "First Name" ve "ID" temsil ettiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="f2e50-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="f2e50-107">Alanlar, öğrencilerin son adlarına göre alfabetik sıralardır.</span><span class="sxs-lookup"><span data-stu-id="f2e50-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="f2e50-108">Sorgu önce KIMLIK sütununun ilk göründüğü yeni bir dizi oluşturur, ardından öğrencinin adı ve soyadı birleştiren ikinci bir sütun gelir.</span><span class="sxs-lookup"><span data-stu-id="f2e50-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="f2e50-109">Satırlar KIMLIK alanına göre yeniden sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="f2e50-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="f2e50-110">Sonuçlar yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="f2e50-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="f2e50-111">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f2e50-111">To create the data file</span></span>  
  
1. <span data-ttu-id="f2e50-112">Aşağıdaki satırları spreadsheet1. csv adlı bir düz metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f2e50-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="f2e50-113">Dosyayı proje klasörünüze kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f2e50-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f2e50-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2e50-114">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2e50-115">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="f2e50-115">Compiling the Code</span></span>  
<span data-ttu-id="f2e50-116">System. C# lınq ve System.IO ad alanları için `using` yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2e50-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f2e50-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e50-117">See also</span></span>

- [<span data-ttu-id="f2e50-118">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="f2e50-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="f2e50-119">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f2e50-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="f2e50-120">CSV dosyalarından XML oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="f2e50-120">How to generate XML from CSV files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
