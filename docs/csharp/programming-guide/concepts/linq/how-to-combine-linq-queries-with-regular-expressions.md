---
title: 'Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme'
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: c535620f2dee1ec9cd1b6ee994fbf860629601ba
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204779"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="0c2f0-102">Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme</span><span class="sxs-lookup"><span data-stu-id="0c2f0-102">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>
<span data-ttu-id="0c2f0-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Text.RegularExpressions.Regex> daha karmaşık metin dizelerini eşleştirme için normal bir ifade oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="0c2f0-104">LINQ Sorgu tam olarak normal ifade ile arama ve sonuçlar şekil için istediğiniz dosyaları filtre kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c2f0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c2f0-105">Example</span></span>  
  
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
  
 <span data-ttu-id="0c2f0-106">Ayrıca Sorgulayabileceğiniz Not <xref:System.Text.RegularExpressions.MatchCollection> tarafından döndürülen nesne gibi bir `RegEx` arama.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="0c2f0-107">Bu örnekte, sonuçları yalnızca her bir eşleşme değeri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="0c2f0-108">Ancak, aynı zamanda filtreleme, sıralama ve gruplandırma bu koleksiyon üzerinde her türlü gerçekleştirmek için LINQ kullanılacak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="0c2f0-109">Çünkü <xref:System.Text.RegularExpressions.MatchCollection> genel olmayan <xref:System.Collections.IEnumerable> koleksiyonuna sahip sorgudaki Aralık değişkeninin türünü açıkça durumuna.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c2f0-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0c2f0-110">Compiling the Code</span></span>  
 <span data-ttu-id="0c2f0-111">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c2f0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c2f0-112">See Also</span></span>

- [<span data-ttu-id="0c2f0-113">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="0c2f0-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [<span data-ttu-id="0c2f0-114">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0c2f0-114">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
