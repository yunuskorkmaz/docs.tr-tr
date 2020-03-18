---
title: Dizin ağacındaki (LINQ) (C#) en büyük dosya veya dosyaları sorgulama
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: ed7d610bd292be4062db89f3c94af280e851141f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168771"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="41047-102">Dizin ağacındaki (LINQ) (C#) en büyük dosya veya dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="41047-102">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="41047-103">Bu örnek, baytlarda dosya boyutuyla ilgili beş sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="41047-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="41047-104">En büyük dosyanın baytboyutu nasıl alınır.</span><span class="sxs-lookup"><span data-stu-id="41047-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="41047-105">En küçük dosyanın baytboyutu nasıl alınır.</span><span class="sxs-lookup"><span data-stu-id="41047-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="41047-106">Nesnenin en <xref:System.IO.FileInfo> büyük veya en küçük dosyasını belirtilen kök klasörün altındaki bir veya daha fazla klasörden alma.</span><span class="sxs-lookup"><span data-stu-id="41047-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="41047-107">En büyük 10 dosya gibi bir sıra nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="41047-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="41047-108">Belirli bir boyuttan daha az dosyaları yoksayarak, baytcinsinden dosya boyutuna göre gruplara dosya siparişi verme.</span><span class="sxs-lookup"><span data-stu-id="41047-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41047-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="41047-109">Example</span></span>  
 <span data-ttu-id="41047-110">Aşağıdaki örnek, baytlarındaki dosya boyutlarına bağlı olarak dosyaların nasıl sorgulanır ve gruplandırılabildiğini gösteren beş ayrı sorgu içerir.</span><span class="sxs-lookup"><span data-stu-id="41047-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="41047-111">Sorguyu <xref:System.IO.FileInfo> nesnenin başka bir özelliğine dayandıracak şekilde bu örnekleri kolayca değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41047-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="41047-112">Bir veya daha <xref:System.IO.FileInfo> fazla tam nesneyi döndürmek için, sorgunun önce veri kaynağındaki her birini incelemesi ve ardından uzunluk özelliğinin değerine göre sıralaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41047-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="41047-113">Sonra tek bir veya en büyük uzunlukları ile sırasını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="41047-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="41047-114">Listedeki ilk öğeyi döndürmek için kullanın. <xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="41047-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="41047-115">İlk <xref:System.Linq.Enumerable.Take%2A> n öğe sayısını döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="41047-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="41047-116">Listenin başındaki en küçük öğeleri koymak için azalan sıralama sırasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="41047-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="41047-117">Sorgu, <xref:System.IO.FileInfo> çağrıda nesnenin oluşturulduğu tarihten bu yana başka bir iş parçacığı üzerinde dosyanın silindiği durumda ortaya çıkacak olası özel durumu tüketmek için baytiçinde dosya boyutunu elde etmek için ayrı bir yönteme `GetFiles`çağırır.</span><span class="sxs-lookup"><span data-stu-id="41047-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="41047-118"><xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine ilk erişici olduğunda baytlarda en güncel boyutu kullanarak özelliğini <xref:System.IO.FileInfo.Length%2A> yenilemeye çalışacağından özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="41047-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="41047-119">Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını uygularız.</span><span class="sxs-lookup"><span data-stu-id="41047-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="41047-120">Genel olarak, bir uygulamabilinmeyen bir durumda bırakılmadığından emin olmak için, özel durumlar tüketirken büyük özen gerekir.</span><span class="sxs-lookup"><span data-stu-id="41047-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41047-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="41047-121">Compiling the Code</span></span>  
<span data-ttu-id="41047-122">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="41047-122">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="41047-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41047-123">See also</span></span>

- [<span data-ttu-id="41047-124">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="41047-124">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="41047-125">LINQ ve Dosya Dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="41047-125">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
