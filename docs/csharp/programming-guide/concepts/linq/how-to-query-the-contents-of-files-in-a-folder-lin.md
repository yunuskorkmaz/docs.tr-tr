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
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a>Bir klasördeki metin dosyalarının içeriği nasıl sorgulanır (LINQ) (C#)
Bu örnek, belirtilen bir dizin ağacındaki tüm dosyaların üzerinde nasıl sorgulanır, her dosyayı açın ve içeriğini nasıl inceleyikarşılarız. Bu tür bir teknik, dizin ağacının içeriğinin dizinlerini oluşturmak veya dizinleri tersine çevirmek için kullanılabilir. Bu örnekte basit bir dize araması gerçekleştirilir. Ancak, normal bir ifade yle daha karmaşık desen eşleştirme türleri gerçekleştirilebilir. Daha fazla bilgi için [LINQ sorgularını normal ifadelerle (C#) nasıl birleştirebilirsiniz'](./how-to-combine-linq-queries-with-regular-expressions.md)e bakın.  
  
## <a name="example"></a>Örnek  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dosya Dizinleri (C#)](./linq-and-file-directories.md)
- [Nesnelere LINQ (C#)](./linq-to-objects.md)
