---
title: Dizin ağacında yinelenen dosyalar için sorgulama (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 1ff5562b-0d30-46d1-b426-a04e8f78c840
ms.openlocfilehash: 0578d6c85c7d2e38c840c278c7ad2775467ac741
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168888"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="71954-102">Dizin ağacında yinelenen dosyalar için sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="71954-102">How to query for duplicate files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="71954-103">Bazen aynı ada sahip dosyalar birden fazla klasörde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="71954-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="71954-104">Örneğin, Visual Studio yükleme klasörü altında, birkaç klasörde readme.htm dosyası bulunur.</span><span class="sxs-lookup"><span data-stu-id="71954-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="71954-105">Bu örnek, bu tür yinelenen dosya adlarının belirli bir kök klasör altında nasıl sorgulanır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="71954-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="71954-106">İkinci örnek, boyutu ve LastWrite süreleri de eşleşen dosyalar için nasıl sorgulanır gösterir.</span><span class="sxs-lookup"><span data-stu-id="71954-106">The second example shows how to query for files whose size and LastWrite times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71954-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="71954-107">Example</span></span>  
  
```csharp  
class QueryDuplicateFileNames  
{  
    static void Main(string[] args)  
    {  
        // Uncomment QueryDuplicates2 to run that query.  
        QueryDuplicates();  
        // QueryDuplicates2();  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    static void QueryDuplicates()  
    {  
        // Change the root drive or folder if necessary  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // used in WriteLine to keep the lines shorter  
        int charsToSkip = startFolder.Length;  
  
        // var can be used for convenience with groups.  
        var queryDupNames =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by file.Name into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        // Pass the query to a method that will  
        // output one page at a time.  
        PageOutput<string, string>(queryDupNames);  
    }  
  
    // A Group key that can be passed to a separate method.  
    // Override Equals and GetHashCode to define equality for the key.  
    // Override ToString to provide a friendly name for Key.ToString()  
    class PortableKey  
    {  
        public string Name { get; set; }  
        public DateTime LastWriteTime { get; set; }  
        public long Length { get; set; }  
  
        public override bool Equals(object obj)  
        {  
            PortableKey other = (PortableKey)obj;  
            return other.LastWriteTime == this.LastWriteTime &&  
                   other.Length == this.Length &&  
                   other.Name == this.Name;  
        }  
  
        public override int GetHashCode()  
        {  
            string str = $"{this.LastWriteTime}{this.Length}{this.Name}";
            return str.GetHashCode();  
        }  
        public override string ToString()  
        {  
            return $"{this.Name} {this.Length} {this.LastWriteTime}";
        }  
    }  
    static void QueryDuplicates2()  
    {  
        // Change the root drive or folder if necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Make the lines shorter for the console display  
        int charsToSkip = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Note the use of a compound key. Files that match  
        // all three properties belong to the same group.  
        // A named type is used to enable the query to be  
        // passed to another method. Anonymous types can also be used  
        // for composite keys but cannot be passed across method boundaries  
        //
        var queryDupFiles =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by  
                new PortableKey { Name = file.Name, LastWriteTime = file.LastWriteTime, Length = file.Length } into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        var list = queryDupFiles.ToList();  
  
        int i = queryDupFiles.Count();  
  
        PageOutput<PortableKey, string>(queryDupFiles);  
    }  
  
    // A generic method to page the output of the QueryDuplications methods  
    // Here the type of the group must be specified explicitly. "var" cannot  
    // be used in method signatures. This method does not display more than one  
    // group per page.  
    private static void PageOutput<K, V>(IEnumerable<System.Linq.IGrouping<K, V>> groupByExtList)  
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
                Console.WriteLine("Filename = {0}", filegroup.Key.ToString() == String.Empty ? "[none]" : filegroup.Key.ToString());  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var fileName in resultPage)  
                {  
                    Console.WriteLine("\t{0}", fileName);  
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
  
 <span data-ttu-id="71954-108">İlk sorgu, eşleşmeyi belirlemek için basit bir anahtar kullanır; bu, aynı ada sahip ancak içeriği farklı olabilecek dosyaları bulur.</span><span class="sxs-lookup"><span data-stu-id="71954-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="71954-109">İkinci sorgu, nesnenin üç özelliğiyle <xref:System.IO.FileInfo> eşleştirmek için bileşik bir anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="71954-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="71954-110">Bu sorgu, aynı ada ve benzer veya aynı içeriğe sahip dosyaları bulmak için çok daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="71954-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71954-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="71954-111">Compiling the Code</span></span>  
 <span data-ttu-id="71954-112">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71954-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71954-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71954-113">See also</span></span>

- [<span data-ttu-id="71954-114">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="71954-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="71954-115">LINQ ve Dosya Dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="71954-115">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
