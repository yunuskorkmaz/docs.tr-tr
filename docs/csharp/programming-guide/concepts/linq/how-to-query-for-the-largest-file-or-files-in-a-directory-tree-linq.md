---
title: Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: dee501dc8d0cabd718307b45c99ca049ae4250aa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344561"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="5d6ff-102">Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5d6ff-102">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="5d6ff-103">Bu örnekte, bayt cinsinden dosya boyutuyla ilgili beş sorgu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5d6ff-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="5d6ff-104">En büyük dosyanın bayt cinsinden boyutunu alma.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="5d6ff-105">En küçük dosyanın bayt cinsinden boyutunu alma.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="5d6ff-106">Belirtilen kök klasörü altındaki bir veya daha fazla klasörden en büyük veya en küçük dosya <xref:System.IO.FileInfo> nesne.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="5d6ff-107">10 en büyük dosya gibi bir sıra alma.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="5d6ff-108">Dosyaları, belirli bir boyuttan daha az olan dosyaları yoksayarak, dosya boyutlarına göre gruplar halinde sıralama.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d6ff-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d6ff-109">Example</span></span>  
 <span data-ttu-id="5d6ff-110">Aşağıdaki örnek, dosya boyutlarına bağlı olarak dosyaların nasıl sorgulandığına ve gruplandıralınacağını gösteren beş ayrı sorgu içerir.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="5d6ff-111">Sorguyu temel alarak <xref:System.IO.FileInfo> nesnesinin diğer bir özelliğinde bu örnekleri kolayca değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="5d6ff-112">Bir veya daha fazla <xref:System.IO.FileInfo> nesnesi döndürmek için, sorgunun her bir veri kaynağında her birini incelemesi gerekir ve sonra bunları length özelliğinin değerine göre sıralayın.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="5d6ff-113">Ardından, en büyük uzunluklara sahip tek bir veya sırası döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="5d6ff-114">Bir listedeki ilk öğeyi döndürmek için <xref:System.Linq.Enumerable.First%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="5d6ff-115">İlk n öğe sayısını döndürmek için <xref:System.Linq.Enumerable.Take%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="5d6ff-116">Listenin başlangıcında en küçük öğeleri yerleştirmek için azalan bir sıralama düzeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="5d6ff-117">Burada bir dosya silindi başka bir iş parçacığında bu yana zaman dönemi içindeki durumda gerçekleştirilecektir olası özel kullanmak bayt cinsinden boyutunu almak için ayrı bir yöntem için sorguyu çağırır <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında`GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="5d6ff-118"><xref:System.IO.FileInfo> nesne zaten oluşturulsa da, bir <xref:System.IO.FileInfo> nesnesi, özelliğin ilk kez eriştiği en güncel boyutu bayt cinsinden <xref:System.IO.FileInfo.Length%2A> yenilemeyi deneyeceğinden, özel durum ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="5d6ff-119">Bu işlemi sorgu dışında bir try-catch bloğuna yerleştirerek, sorguların içindeki işlemleri, yan etkilere neden olabilecek şekilde önleme kuralını izliyoruz.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="5d6ff-120">Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar tüketirken harika bir dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d6ff-121">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="5d6ff-121">Compiling the Code</span></span>  
<span data-ttu-id="5d6ff-122">System. C# lınq ve System.IO ad alanları için `using` yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-122">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="5d6ff-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d6ff-123">See also</span></span>

- [<span data-ttu-id="5d6ff-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="5d6ff-124">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="5d6ff-125">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="5d6ff-125">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
