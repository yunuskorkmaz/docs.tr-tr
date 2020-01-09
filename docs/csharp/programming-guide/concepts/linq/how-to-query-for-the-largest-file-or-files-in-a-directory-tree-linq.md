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
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)
Bu örnekte, bayt cinsinden dosya boyutuyla ilgili beş sorgu gösterilmektedir:  
  
- En büyük dosyanın bayt cinsinden boyutunu alma.  
  
- En küçük dosyanın bayt cinsinden boyutunu alma.  
  
- Belirtilen kök klasörü altındaki bir veya daha fazla klasörden en büyük veya en küçük dosya <xref:System.IO.FileInfo> nesne.  
  
- 10 en büyük dosya gibi bir sıra alma.  
  
- Dosyaları, belirli bir boyuttan daha az olan dosyaları yoksayarak, dosya boyutlarına göre gruplar halinde sıralama.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya boyutlarına bağlı olarak dosyaların nasıl sorgulandığına ve gruplandıralınacağını gösteren beş ayrı sorgu içerir. Sorguyu temel alarak <xref:System.IO.FileInfo> nesnesinin diğer bir özelliğinde bu örnekleri kolayca değiştirebilirsiniz.  
  
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
  
 Bir veya daha fazla <xref:System.IO.FileInfo> nesnesi döndürmek için, sorgunun her bir veri kaynağında her birini incelemesi gerekir ve sonra bunları length özelliğinin değerine göre sıralayın. Ardından, en büyük uzunluklara sahip tek bir veya sırası döndürebilir. Bir listedeki ilk öğeyi döndürmek için <xref:System.Linq.Enumerable.First%2A> kullanın. İlk n öğe sayısını döndürmek için <xref:System.Linq.Enumerable.Take%2A> kullanın. Listenin başlangıcında en küçük öğeleri yerleştirmek için azalan bir sıralama düzeni belirtin.  
  
 Burada bir dosya silindi başka bir iş parçacığında bu yana zaman dönemi içindeki durumda gerçekleştirilecektir olası özel kullanmak bayt cinsinden boyutunu almak için ayrı bir yöntem için sorguyu çağırır <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında`GetFiles`. <xref:System.IO.FileInfo> nesne zaten oluşturulsa da, bir <xref:System.IO.FileInfo> nesnesi, özelliğin ilk kez eriştiği en güncel boyutu bayt cinsinden <xref:System.IO.FileInfo.Length%2A> yenilemeyi deneyeceğinden, özel durum ortaya çıkabilir. Bu işlemi sorgu dışında bir try-catch bloğuna yerleştirerek, sorguların içindeki işlemleri, yan etkilere neden olabilecek şekilde önleme kuralını izliyoruz. Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar tüketirken harika bir dikkatli olunması gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
System. C# lınq ve System.IO ad alanları için `using` yönergeler içeren bir konsol uygulaması projesi oluşturun.
 
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ ve dosya dizinleri (C#)](./linq-and-file-directories.md)
