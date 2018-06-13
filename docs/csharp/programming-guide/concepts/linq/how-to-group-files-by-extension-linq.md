---
title: 'Nasıl yapılır: dosyaları uzantıya (LINQ) (C#) göre gruplama'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 4b2200799a7623bf9d47540f922798f5161be1bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319299"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="2ccfe-102">Nasıl yapılır: dosyaları uzantıya (LINQ) (C#) göre gruplama</span><span class="sxs-lookup"><span data-stu-id="2ccfe-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="2ccfe-103">Bu örnek, Gelişmiş gruplandırma ve sıralama dosya veya klasörleri listelerde işlemleri gerçekleştirmek için LINQ'ın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="2ccfe-104">Ayrıca çıkış konsol penceresinde kullanarak sayfa nasıl gösterir <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ccfe-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ccfe-105">Example</span></span>  
 <span data-ttu-id="2ccfe-106">Aşağıdaki sorgu, dosya adı uzantısı tarafından belirtilen dizin ağacı içeriğini Grup gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2ccfe-107">Bu program çıktısı, yerel dosya sistemi ve ne ayrıntılarını bağlı olarak uzun olabilir `startFolder` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="2ccfe-108">Tüm sonuçlarını görüntülemeyi etkinleştirmek için bu örnek sonuçları sayfası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="2ccfe-109">Windows ve Web uygulamaları için aynı teknikleri uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="2ccfe-110">Bir iç içe bir grup içindeki öğeler kod sayfaları çünkü dikkat `foreach` döngü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="2ccfe-111">İşlem listesinde geçerli konumu ve disk belleği durdurmak ve programdan çıkmak kullanıcı etkinleştirmek için bazı ek mantık yoktur.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="2ccfe-112">Bu örnekte, disk belleği sorgu özgün sorgudan karşı önbelleğe alınan sonuçları çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="2ccfe-113">LINQ-SQL, gibi diğer bağlamlarda böyle önbelleğe alma gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ccfe-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2ccfe-114">Compiling the Code</span></span>  
 <span data-ttu-id="2ccfe-115">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ccfe-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ccfe-116">See Also</span></span>  
 [<span data-ttu-id="2ccfe-117">LINQ to nesneler (C#)</span><span class="sxs-lookup"><span data-stu-id="2ccfe-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="2ccfe-118">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="2ccfe-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
