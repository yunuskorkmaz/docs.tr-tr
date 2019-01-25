---
title: 'Nasıl yapılır: En büyük dosya veya dosyalar sorgu (LINQ) bir dizin ağacındaki (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 20453c754c792d4f5c59fde481e1fec56dcd0e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564139"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="5bb5e-102">Nasıl yapılır: En büyük dosya veya dosyalar sorgu (LINQ) bir dizin ağacındaki (C#)</span><span class="sxs-lookup"><span data-stu-id="5bb5e-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="5bb5e-103">Bu örnek dosyanın bayt cinsinden boyutu ile ilgili beş sorguları gösterir:</span><span class="sxs-lookup"><span data-stu-id="5bb5e-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="5bb5e-104">Bayt cinsinden en büyük dosya boyutu almak nasıl.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="5bb5e-105">En küçük dosyanın bayt cinsinden boyutunu almak nasıl.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="5bb5e-106">Nasıl alınacağını <xref:System.IO.FileInfo> belirtilen kök klasörünün altında bir veya daha fazla klasörlerden nesne en büyük veya küçük dosyası.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="5bb5e-107">10 en büyük dosyaları gibi bir dizi almak nasıl.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="5bb5e-108">Nasıl yapılır sırası dosyaları, dosya boyutu bayt cinsinden göre gruplara belirtilen bir boyuttan daha az olan dosyalar yoksayılıyor.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bb5e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bb5e-109">Example</span></span>  
 <span data-ttu-id="5bb5e-110">Aşağıdaki örnek, sorgulama ve bunların dosya boyutunu bayt cinsinden bağlı olarak, Grup dosyaları göster beş ayrı sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="5bb5e-111">Bu örnekler diğer bazı özellikte sorgu temel kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> nesne.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
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
  
 <span data-ttu-id="5bb5e-112">Bir veya daha fazla tamamlamak döndürülecek <xref:System.IO.FileInfo> nesneler, sorguyu ilk denetleyeceğini her bir veri kaynağı ve sonra bunları kendi uzunluğu özelliğinin değeri sıralayın.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="5bb5e-113">Ardından tek bir ya da ile en fazla uzunluk dizisi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="5bb5e-114">Kullanım <xref:System.Linq.Enumerable.First%2A> listedeki ilk öğe döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="5bb5e-115">Kullanım <xref:System.Linq.Enumerable.Take%2A> ilk n öğe sayısını döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="5bb5e-116">Listenin başında en küçük öğeleri yerleştirmek için azalan sıralama düzeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="5bb5e-117">Burada bir dosya silindi başka bir iş parçacığında bu yana zaman dönemi içindeki durumda gerçekleştirilecektir olası özel kullanmak bayt cinsinden boyutunu almak için ayrı bir yöntem için sorguyu çağırır <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında`GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="5bb5e-118">Bile aracılığıyla <xref:System.IO.FileInfo> nesnesi zaten oluşturuldu, özel durum ortaya çıkabilir çünkü bir <xref:System.IO.FileInfo> nesne yenilemek çalışır, <xref:System.IO.FileInfo.Length%2A> erişilen özelliği ilk kez en geçerli boyutunu bayt cinsinden kullanarak özellik.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="5bb5e-119">Bu işlem bir try-catch bloğunda sorgu dışında koyarak, biz yan etkilere neden olabilecek sorguları işlemlerinde önleme kural izleyin.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="5bb5e-120">Genel olarak, çok dikkatli özel durumlar, tüketildiğinde uygulama bilinmeyen bir durumda kaldı değil emin olmak için özenli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bb5e-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5bb5e-121">Compiling the Code</span></span>  
 <span data-ttu-id="5bb5e-122">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb5e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb5e-123">See also</span></span>

- [<span data-ttu-id="5bb5e-124">LINQ to Objects'in (C#)</span><span class="sxs-lookup"><span data-stu-id="5bb5e-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="5bb5e-125">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="5bb5e-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
