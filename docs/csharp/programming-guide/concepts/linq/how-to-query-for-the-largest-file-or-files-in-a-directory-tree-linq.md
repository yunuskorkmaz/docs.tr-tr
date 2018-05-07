---
title: 'Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 004726c4df1af5a12a411d26c4dc36e1836597ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (C#)
Bu örnek, dosya boyutunu bayt cinsinden ilgili beş sorguları gösterir:  
  
-   Bayt cinsinden en büyük dosya boyutu almak nasıl.  
  
-   Bayt cinsinden en küçük dosya boyutu almak nasıl.  
  
-   Nasıl alınacağını <xref:System.IO.FileInfo> belirtilen kök klasörü altında bir veya daha fazla klasörlerden nesne büyük veya en küçük dosya.  
  
-   10 büyük dosyaları gibi bir dizi almak nasıl.  
  
-   Belirtilen bir boyuttan daha küçük olan dosyaları yoksayılıyor kendi dosya boyutunu bayt cinsinden dayanarak gruplara sipariş dosyaları nasıl.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgulama ve grup dosyaları, kendi dosya boyutunu bayt cinsinden bağlı olarak göster beş ayrı sorguları içerir. Bu örnekler diğer bazı özellikte sorguyu temel kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> nesnesi.  
  
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
  
 Bir veya daha fazla tamamlamak döndürülecek <xref:System.IO.FileInfo> nesneleri, sorgu ilk denetleyeceğini her bir veri kaynağı ve ardından bunları kendi uzunluğu özellik değerine göre sıralama. Ardından tek tek veya ile en büyük uzunluk dizisi döndürebilir. Kullanım <xref:System.Linq.Enumerable.First%2A> listedeki ilk öğe dönün. Kullanım <xref:System.Linq.Enumerable.Take%2A> ilk n öğe sayısını döndürmek için. Listenin başında küçük öğeleri yerleştirmek için azalan sıralama düzeni belirtin.  
  
 Sorgu burada bir dosya silindi başka bir iş parçacığında bu yana sürede durumda gerçekleştirilecektir olası özel kullanmak için dosyanın bayt cinsinden boyutu almak için ayrı bir yöntem çağırır <xref:System.IO.FileInfo> nesne çağrısındaoluşturulduğu`GetFiles`. Bile aracılığıyla <xref:System.IO.FileInfo> nesnesi zaten oluşturulmuş, özel durumu oluşabilir çünkü bir <xref:System.IO.FileInfo> nesne Yenile deneyecek kendi <xref:System.IO.FileInfo.Length%2A> özelliği erişildiğinde ilk kez en güncel boyutunu bayt cinsinden kullanarak özelliği. Try-catch bloğunda sorgu dışında bu işlemi koyarak, biz yan etkileri neden olan sorguları işlemlerinde önleme kural izleyin. Genel olarak, çok dikkatli özel durumlar, kullanırken bir uygulama bilinmeyen bir durumda sol değil emin olmak için izlenmelidir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
