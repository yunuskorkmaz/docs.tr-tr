---
title: 'Nasıl yapılır: metin dosyaları (LINQ) (C#) bir klasörde içeriğini sorgulama'
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: dedb3b742805daa23151c61e89dd0835f730dd9c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270170"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a>Nasıl yapılır: metin dosyaları (LINQ) (C#) bir klasörde içeriğini sorgulama
Bu örnek, belirtilen dizin ağacındaki tüm dosyalar üzerinde sorgulama, her dosyasını açın ve içeriğini inceleyin gösterilmektedir. Bu tür bir teknik dizinler oluşturmak veya bir dizin ağacında içeriği dizinlerini tersine çevirecek şekilde kullanılabilir. Bu örnekte basit dize arama gerçekleştirilir. Ancak, daha karmaşık tür deseniyle eşleşen normal bir ifade ile gerçekleştirilebilir. Daha fazla bilgi için [nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).  
  
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
 .NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
