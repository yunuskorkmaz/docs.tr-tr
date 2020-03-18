---
title: Bir klasördeki metin dosyalarının içeriği nasıl sorgulanır (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 998fddd3f59ee64df9adcee1acc720d82861c3d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168745"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="b5ee7-102">Bir klasördeki metin dosyalarının içeriği nasıl sorgulanır (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b5ee7-102">How to query the contents of text files in a folder (LINQ) (C#)</span></span>
<span data-ttu-id="b5ee7-103">Bu örnek, belirtilen bir dizin ağacındaki tüm dosyaların üzerinde nasıl sorgulanır, her dosyayı açın ve içeriğini nasıl inceleyikarşılarız.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="b5ee7-104">Bu tür bir teknik, dizin ağacının içeriğinin dizinlerini oluşturmak veya dizinleri tersine çevirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="b5ee7-105">Bu örnekte basit bir dize araması gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="b5ee7-106">Ancak, normal bir ifade yle daha karmaşık desen eşleştirme türleri gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="b5ee7-107">Daha fazla bilgi için [LINQ sorgularını normal ifadelerle (C#) nasıl birleştirebilirsiniz'](./how-to-combine-linq-queries-with-regular-expressions.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-107">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5ee7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5ee7-108">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5ee7-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b5ee7-109">Compiling the Code</span></span>  
<span data-ttu-id="b5ee7-110">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b5ee7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5ee7-111">See also</span></span>

- [<span data-ttu-id="b5ee7-112">LINQ ve Dosya Dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b5ee7-112">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="b5ee7-113">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="b5ee7-113">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
