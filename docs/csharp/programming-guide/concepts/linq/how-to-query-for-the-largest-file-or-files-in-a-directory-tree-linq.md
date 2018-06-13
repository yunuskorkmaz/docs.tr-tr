---
title: 'Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 004726c4df1af5a12a411d26c4dc36e1836597ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325363"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="47046-102">Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="47046-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="47046-103">Bu örnek, dosya boyutunu bayt cinsinden ilgili beş sorguları gösterir:</span><span class="sxs-lookup"><span data-stu-id="47046-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="47046-104">Bayt cinsinden en büyük dosya boyutu almak nasıl.</span><span class="sxs-lookup"><span data-stu-id="47046-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="47046-105">Bayt cinsinden en küçük dosya boyutu almak nasıl.</span><span class="sxs-lookup"><span data-stu-id="47046-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="47046-106">Nasıl alınacağını <xref:System.IO.FileInfo> belirtilen kök klasörü altında bir veya daha fazla klasörlerden nesne büyük veya en küçük dosya.</span><span class="sxs-lookup"><span data-stu-id="47046-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="47046-107">10 büyük dosyaları gibi bir dizi almak nasıl.</span><span class="sxs-lookup"><span data-stu-id="47046-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="47046-108">Belirtilen bir boyuttan daha küçük olan dosyaları yoksayılıyor kendi dosya boyutunu bayt cinsinden dayanarak gruplara sipariş dosyaları nasıl.</span><span class="sxs-lookup"><span data-stu-id="47046-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47046-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="47046-109">Example</span></span>  
 <span data-ttu-id="47046-110">Aşağıdaki örnek, sorgulama ve grup dosyaları, kendi dosya boyutunu bayt cinsinden bağlı olarak göster beş ayrı sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="47046-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="47046-111">Bu örnekler diğer bazı özellikte sorguyu temel kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="47046-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="47046-112">Bir veya daha fazla tamamlamak döndürülecek <xref:System.IO.FileInfo> nesneleri, sorgu ilk denetleyeceğini her bir veri kaynağı ve ardından bunları kendi uzunluğu özellik değerine göre sıralama.</span><span class="sxs-lookup"><span data-stu-id="47046-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="47046-113">Ardından tek tek veya ile en büyük uzunluk dizisi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="47046-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="47046-114">Kullanım <xref:System.Linq.Enumerable.First%2A> listedeki ilk öğe dönün.</span><span class="sxs-lookup"><span data-stu-id="47046-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="47046-115">Kullanım <xref:System.Linq.Enumerable.Take%2A> ilk n öğe sayısını döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="47046-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="47046-116">Listenin başında küçük öğeleri yerleştirmek için azalan sıralama düzeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="47046-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="47046-117">Sorgu burada bir dosya silindi başka bir iş parçacığında bu yana sürede durumda gerçekleştirilecektir olası özel kullanmak için dosyanın bayt cinsinden boyutu almak için ayrı bir yöntem çağırır <xref:System.IO.FileInfo> nesne çağrısındaoluşturulduğu`GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="47046-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="47046-118">Bile aracılığıyla <xref:System.IO.FileInfo> nesnesi zaten oluşturulmuş, özel durumu oluşabilir çünkü bir <xref:System.IO.FileInfo> nesne Yenile deneyecek kendi <xref:System.IO.FileInfo.Length%2A> özelliği erişildiğinde ilk kez en güncel boyutunu bayt cinsinden kullanarak özelliği.</span><span class="sxs-lookup"><span data-stu-id="47046-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="47046-119">Try-catch bloğunda sorgu dışında bu işlemi koyarak, biz yan etkileri neden olan sorguları işlemlerinde önleme kural izleyin.</span><span class="sxs-lookup"><span data-stu-id="47046-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="47046-120">Genel olarak, çok dikkatli özel durumlar, kullanırken bir uygulama bilinmeyen bir durumda sol değil emin olmak için izlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="47046-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47046-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="47046-121">Compiling the Code</span></span>  
 <span data-ttu-id="47046-122">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="47046-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47046-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47046-123">See Also</span></span>  
 [<span data-ttu-id="47046-124">LINQ to nesneler (C#)</span><span class="sxs-lookup"><span data-stu-id="47046-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="47046-125">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="47046-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
