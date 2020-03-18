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
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Dizin ağacındaki (LINQ) (C#) en büyük dosya veya dosyaları sorgulama
Bu örnek, baytlarda dosya boyutuyla ilgili beş sorgu gösterir:  
  
- En büyük dosyanın baytboyutu nasıl alınır.  
  
- En küçük dosyanın baytboyutu nasıl alınır.  
  
- Nesnenin en <xref:System.IO.FileInfo> büyük veya en küçük dosyasını belirtilen kök klasörün altındaki bir veya daha fazla klasörden alma.  
  
- En büyük 10 dosya gibi bir sıra nasıl alınır?  
  
- Belirli bir boyuttan daha az dosyaları yoksayarak, baytcinsinden dosya boyutuna göre gruplara dosya siparişi verme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, baytlarındaki dosya boyutlarına bağlı olarak dosyaların nasıl sorgulanır ve gruplandırılabildiğini gösteren beş ayrı sorgu içerir. Sorguyu <xref:System.IO.FileInfo> nesnenin başka bir özelliğine dayandıracak şekilde bu örnekleri kolayca değiştirebilirsiniz.  
  
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
  
 Bir veya daha <xref:System.IO.FileInfo> fazla tam nesneyi döndürmek için, sorgunun önce veri kaynağındaki her birini incelemesi ve ardından uzunluk özelliğinin değerine göre sıralaması gerekir. Sonra tek bir veya en büyük uzunlukları ile sırasını döndürebilir. Listedeki ilk öğeyi döndürmek için kullanın. <xref:System.Linq.Enumerable.First%2A> İlk <xref:System.Linq.Enumerable.Take%2A> n öğe sayısını döndürmek için kullanın. Listenin başındaki en küçük öğeleri koymak için azalan sıralama sırasını belirtin.  
  
 Sorgu, <xref:System.IO.FileInfo> çağrıda nesnenin oluşturulduğu tarihten bu yana başka bir iş parçacığı üzerinde dosyanın silindiği durumda ortaya çıkacak olası özel durumu tüketmek için baytiçinde dosya boyutunu elde etmek için ayrı bir yönteme `GetFiles`çağırır. <xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine ilk erişici olduğunda baytlarda en güncel boyutu kullanarak özelliğini <xref:System.IO.FileInfo.Length%2A> yenilemeye çalışacağından özel durum oluşabilir. Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını uygularız. Genel olarak, bir uygulamabilinmeyen bir durumda bırakılmadığından emin olmak için, özel durumlar tüketirken büyük özen gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (C#)](./linq-to-objects.md)
- [LINQ ve Dosya Dizinleri (C#)](./linq-and-file-directories.md)
