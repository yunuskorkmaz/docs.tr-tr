---
title: LINQ sorgularını normal ifadelerle birleştirme (C#)
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: 104e63adb9c07a75077b92654afd791b6c82d8de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169435"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a>LINQ sorgularını normal ifadelerle birleştirme (C#)
Bu örnek, metin <xref:System.Text.RegularExpressions.Regex> dizelerinde daha karmaşık eşleştirme için normal bir ifade oluşturmak için sınıfın nasıl kullanılacağını gösterir. LINQ sorgusu, normal ifadeyle aramak istediğiniz dosyalara tam olarak filtre uygulamanızı ve sonuçları şekillendirmeyi kolaylaştırır.  
  
## <a name="example"></a>Örnek  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 Arama tarafından döndürülen <xref:System.Text.RegularExpressions.MatchCollection> nesneyi de sorgulayabildiğinizi unutmayın. `RegEx` Bu örnekte sonuçlarda yalnızca her eşleşmenin değeri üretilir. Ancak, linq'i kullanarak bu koleksiyonda her türlü filtreleme, sıralama ve gruplandırma yı gerçekleştirmek de mümkündür. Genel <xref:System.Text.RegularExpressions.MatchCollection> <xref:System.Collections.IEnumerable> olmayan bir koleksiyon olduğundan, sorgudaki aralık değişkeninin türünü açıkça belirtmeniz gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dizeleri (C#)](./linq-and-strings.md)
- [LINQ ve Dosya Dizinleri (C#)](./linq-and-file-directories.md)
