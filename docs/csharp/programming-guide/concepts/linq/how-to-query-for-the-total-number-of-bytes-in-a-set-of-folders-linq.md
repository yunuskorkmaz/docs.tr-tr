---
title: Bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (C#)
description: Belirli bir klasörde ve alt klasörlerinde bulunan tüm dosyalar tarafından kullanılan toplam bayt sayısını bulmak Için C# ' de LINQ kullanmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 562fd32ad9e9040a5898322d840718f25b56e2cd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159039"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="0d421-103">Bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0d421-103">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>

<span data-ttu-id="0d421-104">Bu örnek, belirtilen bir klasör ve tüm alt klasörlerindeki tüm dosyalar tarafından kullanılan toplam bayt sayısının nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d421-104">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d421-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d421-105">Example</span></span>  

 <span data-ttu-id="0d421-106"><xref:System.Linq.Enumerable.Sum%2A>Yöntemi, yan tümcesinde seçili olan tüm öğelerin değerlerini ekler `select` .</span><span class="sxs-lookup"><span data-stu-id="0d421-106">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="0d421-107">Yerine veya metodunu çağırarak, belirtilen dizin ağacındaki en büyük veya en küçük dosyayı almak için bu sorguyu kolayca değiştirebilirsiniz <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Sum%2A> .</span><span class="sxs-lookup"><span data-stu-id="0d421-107">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="0d421-108">Yalnızca belirtilen bir dizin ağacındaki bayt sayısını saymanız gerekiyorsa, bunu bir veri kaynağı olarak liste koleksiyonu oluşturma ek yükünü bir LINQ sorgusu oluşturmadan daha verimli bir şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d421-108">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="0d421-109">Sorgu daha karmaşık hale geldiği veya aynı veri kaynağında birden çok sorgu çalıştırmanız gerektiğinde LINQ yaklaşımın Yararlılığı artar.</span><span class="sxs-lookup"><span data-stu-id="0d421-109">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="0d421-110">Sorgu, dosya uzunluğunu elde etmek için ayrı bir yönteme çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="0d421-110">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="0d421-111">Bu, dosya, öğesine yapılan çağrıda oluşturulduktan sonra başka bir iş parçacığında silinmişse, ortaya çıkan olası özel durumu kullanmak için bunu yapar <xref:System.IO.FileInfo> `GetFiles` .</span><span class="sxs-lookup"><span data-stu-id="0d421-111">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="0d421-112"><xref:System.IO.FileInfo>Nesne zaten oluşturulmuş olsa da, bir nesne, özelliği <xref:System.IO.FileInfo> <xref:System.IO.FileInfo.Length%2A> ilk kez erişildiği zaman en güncel uzunlukla yenilemeyi deneyeceğinden, özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="0d421-112">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="0d421-113">Bu işlemi sorgu dışında bir try-catch bloğuna koyarak, kod, yan etkilere neden olabilecek sorgularda işlemleri önleme kuralına uyar.</span><span class="sxs-lookup"><span data-stu-id="0d421-113">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="0d421-114">Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar kullandığınızda harika dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d421-114">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d421-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0d421-115">Compiling the Code</span></span>  

<span data-ttu-id="0d421-116">`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0d421-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0d421-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d421-117">See also</span></span>

- [<span data-ttu-id="0d421-118">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="0d421-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="0d421-119">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0d421-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
