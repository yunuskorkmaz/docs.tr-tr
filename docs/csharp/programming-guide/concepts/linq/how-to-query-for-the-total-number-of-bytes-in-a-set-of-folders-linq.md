---
title: 'Nasıl yapılır: sorgu klasörleri (LINQ) (C#) bir dizi bayt toplam sayısı'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 7a11e30a41ce171d516d3ea00a0e8664efe33520
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135191"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="dd8bf-102">Nasıl yapılır: sorgu klasörleri (LINQ) (C#) bir dizi bayt toplam sayısı</span><span class="sxs-lookup"><span data-stu-id="dd8bf-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="dd8bf-103">Bu örnek belirtilen bir klasördeki tüm dosyaları ve tüm alt klasörleri tarafından kullanılan bayt toplam sayısını almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd8bf-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd8bf-104">Example</span></span>  
 <span data-ttu-id="dd8bf-105"><xref:System.Linq.Enumerable.Sum%2A> Yöntemi, seçilen tüm öğelerin değerini ekler `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="dd8bf-106">Belirtilen dizin ağacındaki en büyük veya en küçük dosya çağırarak almak için bu sorguyu kolayca değiştirebilirsiniz <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> yöntemi yerine <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="dd8bf-107">Yalnızca belirtilen dizin ağacı bayt sayısını varsa, daha verimli bir şekilde bir veri kaynağı olarak liste koleksiyonu oluşturma işleminin ek yüke neden olur bir LINQ Sorgu oluşturmadan bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="dd8bf-108">Sorguyu daha karmaşık hale geldiğinde veya aynı veri kaynağında birden çok sorguları çalıştırmak sahip olduğunda LINQ yaklaşım kullanışlılığını artırır.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="dd8bf-109">Sorgu dosya uzunluğu elde etmek için ayrı bir yöntemi için çağırır.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="dd8bf-110">Dosya başka bir iş parçacığında sonra silinmişse, oluşturulur ve olası özel kullanmak için bunu yapar <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="dd8bf-111">Olsa bile <xref:System.IO.FileInfo> nesnesi zaten oluşturuldu, özel durum ortaya çıkabilir çünkü bir <xref:System.IO.FileInfo> nesne yenilemek çalışır, <xref:System.IO.FileInfo.Length%2A> özelliği ile erişilen özelliği ilk kez en güncel uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="dd8bf-112">Bir try-catch bloğunda sorgu dışında bu işlemi koyarak kod yan etkilere neden olabilecek sorguları işlemlerinde önleme kuralı izler.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="dd8bf-113">Genel olarak, bir uygulama bilinmeyen bir durumda kaldı değil emin olmak için özel durumlar tükettiğinizde çok dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd8bf-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dd8bf-114">Compiling the Code</span></span>  
 <span data-ttu-id="dd8bf-115">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8bf-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd8bf-116">See Also</span></span>

- [<span data-ttu-id="dd8bf-117">LINQ to Objects'in (C#)</span><span class="sxs-lookup"><span data-stu-id="dd8bf-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="dd8bf-118">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="dd8bf-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
