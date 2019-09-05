---
title: 'Nasıl yapılır: Grupları (LINQ) kullanarak bir dosyayı çok sayıda dosyaya bölme (LINQC#) ()'
ms.date: 07/20/2015
ms.assetid: 8179b91c-d778-4e57-884f-77fe5a8e4e40
ms.openlocfilehash: 5f2ae7657162ba5a2c88e5378119eaad4cb1e288
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253272"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-c"></a><span data-ttu-id="d7e00-102">Nasıl yapılır: Grupları (LINQ) kullanarak bir dosyayı çok sayıda dosyaya bölme (LINQC#) ()</span><span class="sxs-lookup"><span data-stu-id="d7e00-102">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>
<span data-ttu-id="d7e00-103">Bu örnek, iki dosyanın içeriğini birleştirmenin bir yolunu gösterir ve ardından verileri yeni bir şekilde düzenleyen yeni bir dosya kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7e00-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="d7e00-104">Veri dosyalarını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7e00-104">To create the data files</span></span>  
  
1. <span data-ttu-id="d7e00-105">Bu adları names1. txt adlı bir metin dosyasına kopyalayın ve proje klasörünüze kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d7e00-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. <span data-ttu-id="d7e00-106">Bu adları names2. txt adlı bir metin dosyasına kopyalayın ve proje klasörünüze kaydedin: İki dosyanın bazı adları yaygın olarak olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d7e00-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="d7e00-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7e00-107">Example</span></span>  
  
```csharp  
class SplitWithGroups  
{  
    static void Main()  
    {  
        string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Concatenate and remove duplicate names based on  
        // default string comparer  
        var mergeQuery = fileA.Union(fileB);  
  
        // Group the names by the first letter in the last name.  
        var groupQuery = from name in mergeQuery  
                         let n = name.Split(',')  
                         group name by n[0][0] into g  
                         orderby g.Key  
                         select g;  
  
        // Create a new file for each group that was created  
        // Note that nested foreach loops are required to access  
        // individual items with each group.  
        foreach (var g in groupQuery)  
        {  
            // Create the new file name.  
            string fileName = @"../../../testFile_" + g.Key + ".txt";  
  
            // Output to display.  
            Console.WriteLine(g.Key);  
  
            // Write file.  
            using (System.IO.StreamWriter sw = new System.IO.StreamWriter(fileName))  
            {  
                foreach (var item in g)  
                {  
                    sw.WriteLine(item);  
                    // Output to console for example purposes.  
                    Console.WriteLine("   {0}", item);  
                }  
            }  
        }  
        // Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:   
    A  
       Aw, Kam Foo  
    B  
       Bankov, Peter  
       Beebe, Ann  
    E  
       El Yassir, Mehdi  
    G  
       Garcia, Hugo  
       Guy, Wey Yuan  
       Garcia, Debra  
       Gilchrist, Beth  
       Giakoumakis, Leo  
    H  
       Holm, Michael  
    L  
       Liu, Jinghao  
    M  
       Myrcha, Jacek  
       McLin, Nkenge  
    N  
       Noriega, Fabricio  
    P  
       Potra, Cristina  
    T  
       Toyoshima, Tim  
 */  
```  
  
 <span data-ttu-id="d7e00-108">Program, veri dosyalarıyla aynı klasöre her bir grup için ayrı bir dosya yazar.</span><span class="sxs-lookup"><span data-stu-id="d7e00-108">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7e00-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d7e00-109">Compiling the Code</span></span>

<span data-ttu-id="d7e00-110">System. C# LINQ ve System.IO ad alanları `using` için yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7e00-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d7e00-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e00-111">See also</span></span>

- [<span data-ttu-id="d7e00-112">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="d7e00-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="d7e00-113">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d7e00-113">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
