---
title: Ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)
description: C# ' de LINQ içindeki bir. csv dosyasındaki alanları yeniden düzenleme hakkında bilgi edinin. Örnek sütun ve sütunları bir sütun değerine göre sıralar.
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 3ebc56b418d2732a296896a19d770136a56e2fbb
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103411"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="ac129-104">Ayrılmış bir dosyanın alanlarını yeniden sıralama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ac129-104">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="ac129-105">Virgülle ayrılmış değer (CSV) dosyası, elektronik tablo verilerini veya satırlar ve sütunlar tarafından temsil edilen diğer tablo verilerini depolamak için genellikle kullanılan bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ac129-105">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="ac129-106"><xref:System.String.Split%2A>Alanları ayırmak için yöntemini kullanarak, LINQ kullanarak CSV dosyalarını sorgulamak ve işlemek çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ac129-106">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="ac129-107">Aslında, yapılandırılmış herhangi bir metin satırının parçalarını yeniden sıralamak için aynı teknik de kullanılabilir; CSV dosyalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="ac129-107">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="ac129-108">Aşağıdaki örnekte, üç sütunun öğrencileri ' "soyadı," "First Name" ve "ID" temsil ettiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="ac129-108">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="ac129-109">Alanlar, öğrencilerin son adlarına göre alfabetik sıralardır.</span><span class="sxs-lookup"><span data-stu-id="ac129-109">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="ac129-110">Sorgu önce KIMLIK sütununun ilk göründüğü yeni bir dizi oluşturur, ardından öğrencinin adı ve soyadı birleştiren ikinci bir sütun gelir.</span><span class="sxs-lookup"><span data-stu-id="ac129-110">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="ac129-111">Satırlar KIMLIK alanına göre yeniden sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="ac129-111">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="ac129-112">Sonuçlar yeni bir dosyaya kaydedilir ve özgün veriler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="ac129-112">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="ac129-113">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ac129-113">To create the data file</span></span>  
  
1. <span data-ttu-id="ac129-114">Aşağıdaki satırları spreadsheet1.csv adında bir düz metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ac129-114">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="ac129-115">Dosyayı proje klasörünüze kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ac129-115">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ac129-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac129-116">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac129-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ac129-117">Compiling the Code</span></span>  
<span data-ttu-id="ac129-118">`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac129-118">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ac129-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac129-119">See also</span></span>

- [<span data-ttu-id="ac129-120">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="ac129-120">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="ac129-121">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="ac129-121">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="ac129-122">CSV dosyalarından XML oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="ac129-122">How to generate XML from CSV files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
