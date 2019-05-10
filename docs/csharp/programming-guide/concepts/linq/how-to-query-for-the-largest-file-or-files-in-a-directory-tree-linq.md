---
title: 'Nasıl yapılır: En büyük dosya veya dosyalar sorgu (LINQ) bir dizin ağacındaki (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 134183da58b490635284699de2f1721dda5422dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597067"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Nasıl yapılır: En büyük dosya veya dosyalar sorgu (LINQ) bir dizin ağacındaki (C#)
Bu örnek dosyanın bayt cinsinden boyutu ile ilgili beş sorguları gösterir:  
  
- Bayt cinsinden en büyük dosya boyutu almak nasıl.  
  
- En küçük dosyanın bayt cinsinden boyutunu almak nasıl.  
  
- Nasıl alınacağını <xref:System.IO.FileInfo> belirtilen kök klasörünün altında bir veya daha fazla klasörlerden nesne en büyük veya küçük dosyası.  
  
- 10 en büyük dosyaları gibi bir dizi almak nasıl.  
  
- Nasıl yapılır sırası dosyaları, dosya boyutu bayt cinsinden göre gruplara belirtilen bir boyuttan daha az olan dosyalar yoksayılıyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgulama ve bunların dosya boyutunu bayt cinsinden bağlı olarak, Grup dosyaları göster beş ayrı sorguları içerir. Bu örnekler diğer bazı özellikte sorgu temel kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> nesne.  
  
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
  
 Bir veya daha fazla tamamlamak döndürülecek <xref:System.IO.FileInfo> nesneler, sorguyu ilk denetleyeceğini her bir veri kaynağı ve sonra bunları kendi uzunluğu özelliğinin değeri sıralayın. Ardından tek bir ya da ile en fazla uzunluk dizisi döndürebilir. Kullanım <xref:System.Linq.Enumerable.First%2A> listedeki ilk öğe döndürmek için. Kullanım <xref:System.Linq.Enumerable.Take%2A> ilk n öğe sayısını döndürmek için. Listenin başında en küçük öğeleri yerleştirmek için azalan sıralama düzeni belirtin.  
  
 Burada bir dosya silindi başka bir iş parçacığında bu yana zaman dönemi içindeki durumda gerçekleştirilecektir olası özel kullanmak bayt cinsinden boyutunu almak için ayrı bir yöntem için sorguyu çağırır <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında`GetFiles`. Bile aracılığıyla <xref:System.IO.FileInfo> nesnesi zaten oluşturuldu, özel durum ortaya çıkabilir çünkü bir <xref:System.IO.FileInfo> nesne yenilemek çalışır, <xref:System.IO.FileInfo.Length%2A> erişilen özelliği ilk kez en geçerli boyutunu bayt cinsinden kullanarak özellik. Bu işlem bir try-catch bloğunda sorgu dışında koyarak, biz yan etkilere neden olabilecek sorguları işlemlerinde önleme kural izleyin. Genel olarak, çok dikkatli özel durumlar, tüketildiğinde uygulama bilinmeyen bir durumda kaldı değil emin olmak için özenli olunması gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
