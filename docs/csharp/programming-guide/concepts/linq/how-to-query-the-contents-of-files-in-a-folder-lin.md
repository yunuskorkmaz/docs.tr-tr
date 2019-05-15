---
title: 'Nasıl yapılır: Bir klasör (LINQ) metin dosyalarında içeriğini sorgulama (C#)'
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 1be896f257395cb1e70718ac55e3199da09d8961
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585844"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="8e609-102">Nasıl yapılır: Bir klasör (LINQ) metin dosyalarında içeriğini sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="8e609-102">How to: Query the Contents of Text Files in a Folder (LINQ) (C#)</span></span>
<span data-ttu-id="8e609-103">Bu örnek, belirtilen dizin ağacındaki tüm dosyalar üzerinde sorgulama, her dosyasını açın ve içeriğini inceleyin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8e609-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="8e609-104">Bu tür bir teknik dizinler oluşturmak veya bir dizin ağacında içeriği dizinlerini tersine çevirecek şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e609-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="8e609-105">Bu örnekte basit dize arama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8e609-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="8e609-106">Ancak, daha karmaşık tür deseniyle eşleşen normal bir ifade ile gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e609-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="8e609-107">Daha fazla bilgi için [nasıl yapılır: Normal ifadelerle LINQ sorgularını birleştirme (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8e609-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e609-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e609-108">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e609-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8e609-109">Compiling the Code</span></span>  
<span data-ttu-id="8e609-110">Oluşturma bir C# konsol uygulama projesi ile `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="8e609-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8e609-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e609-111">See also</span></span>

- [<span data-ttu-id="8e609-112">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8e609-112">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="8e609-113">LINQ to Objects'in (C#)</span><span class="sxs-lookup"><span data-stu-id="8e609-113">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
