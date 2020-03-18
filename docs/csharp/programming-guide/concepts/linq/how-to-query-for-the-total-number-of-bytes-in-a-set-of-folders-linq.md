---
title: Klasörler kümesindeki toplam bayt sayısı (LINQ) (C#) için sorgulama
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: c6bfe6bb6d76e7ce8ea8887eef85cd64f2a025df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344825"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="c4f3b-102">Klasörler kümesindeki toplam bayt sayısı (LINQ) (C#) için sorgulama</span><span class="sxs-lookup"><span data-stu-id="c4f3b-102">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>
<span data-ttu-id="c4f3b-103">Bu örnek, belirtilen bir klasördeki tüm dosyalar ve tüm alt klasörleri tarafından kullanılan toplam bayt sayısını nasıl alsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4f3b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4f3b-104">Example</span></span>  
 <span data-ttu-id="c4f3b-105">Yöntem, <xref:System.Linq.Enumerable.Sum%2A> `select` yan tümcede seçilen tüm öğelerin değerlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="c4f3b-106">Bu sorguyu, belirtilen dizin ağacındaki en büyük veya en küçük <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> dosyayı <xref:System.Linq.Enumerable.Sum%2A>almak için kolayca değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="c4f3b-107">Yalnızca belirli bir dizin ağacındaki bayt sayısını saymanız gerekiyorsa, bunu, liste koleksiyonunu veri kaynağı olarak oluşturma nın ek yüküne neden olan bir LINQ sorgusu oluşturmadan daha verimli bir şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="c4f3b-108">Sorgu daha karmaşık hale geldikçe veya aynı veri kaynağına karşı birden çok sorgu çalıştırmanız gerektiğinde LINQ yaklaşımının kullanışlılığı artar.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="c4f3b-109">Sorgu, dosya uzunluğunu elde etmek için ayrı bir yönteme çağırır.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="c4f3b-110">Bunu, <xref:System.IO.FileInfo> çağrıda nesne oluşturulduktan sonra dosya başka bir iş parçacığı üzerinde silinmişse yükseltilecek olası özel durumu tüketmek için `GetFiles`yapar.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="c4f3b-111"><xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine <xref:System.IO.FileInfo.Length%2A> ilk erişilen en geçerli uzunlukta yenilenmeye çalışacağından özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="c4f3b-112">Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, kod yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını izler.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="c4f3b-113">Genel olarak, bir uygulamanın bilinmeyen bir durumda bırakılmadığından emin olmak için özel durumları tükettiğinizde büyük özen gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4f3b-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c4f3b-114">Compiling the Code</span></span>  
<span data-ttu-id="c4f3b-115">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c4f3b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4f3b-116">See also</span></span>

- [<span data-ttu-id="c4f3b-117">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="c4f3b-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="c4f3b-118">LINQ ve Dosya Dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="c4f3b-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
