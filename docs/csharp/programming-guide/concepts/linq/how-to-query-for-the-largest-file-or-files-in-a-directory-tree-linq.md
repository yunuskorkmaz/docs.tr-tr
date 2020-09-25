---
title: Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)
description: Bu C# örneğinde, bayt cinsinden dosya boyutuyla ilgili beş LINQ sorgusu gösterilmektedir. Bunları, Info nesnesinin diğer bir özelliğinde sorgulamak için değiştirebilirsiniz.
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 049db9bf104af1593ba9807c307008e8e760da32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176259"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)

Bu örnekte, bayt cinsinden dosya boyutuyla ilgili beş sorgu gösterilmektedir:  
  
- En büyük dosyanın bayt cinsinden boyutunu alma.  
  
- En küçük dosyanın bayt cinsinden boyutunu alma.  
  
- <xref:System.IO.FileInfo>Belirtilen kök klasörü altındaki bir veya daha fazla klasörden en büyük veya en küçük dosyayı alma.  
  
- 10 en büyük dosya gibi bir sıra alma.  
  
- Dosyaları, belirli bir boyuttan daha az olan dosyaları yoksayarak, dosya boyutlarına göre gruplar halinde sıralama.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, dosya boyutlarına bağlı olarak dosyaların nasıl sorgulandığına ve gruplandıralınacağını gösteren beş ayrı sorgu içerir. Bu örnekleri, sorgunun diğer bir özelliğindeki sorgu temel alınarak kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> .  
  
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
  
 Bir veya daha fazla tamamlanmış nesne döndürmek için <xref:System.IO.FileInfo> , sorgunun her birini veri kaynağında incelemesi gerekir ve sonra bunları length özelliğinin değerine göre sıralayın. Ardından, en büyük uzunluklara sahip tek bir veya sırası döndürebilir. <xref:System.Linq.Enumerable.First%2A>Bir listedeki ilk öğeyi döndürmek için kullanın. <xref:System.Linq.Enumerable.Take%2A>İlk n öğe sayısını döndürmek için kullanın. Listenin başlangıcında en küçük öğeleri yerleştirmek için azalan bir sıralama düzeni belirtin.  
  
 Sorgu ayrı bir yönteme, dosya boyutunu bir dosyanın silindiği bir zaman diliminde başka bir iş parçacığında silinmiş olması durumunda oluşturulacak olası özel durumu tüketmek için bir kez çağırır <xref:System.IO.FileInfo> `GetFiles` . <xref:System.IO.FileInfo>Nesne zaten oluşturulsa da, bir nesne, özelliğin <xref:System.IO.FileInfo> <xref:System.IO.FileInfo.Length%2A> ilk kez en güncel boyutunu bayt olarak yenilemeyi deneyeceğinden, özel durum oluşabilir. Bu işlemi sorgu dışında bir try-catch bloğuna yerleştirerek, sorguların içindeki işlemleri, yan etkilere neden olabilecek şekilde önleme kuralını izliyoruz. Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar tüketirken harika bir dikkatli olunması gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ ve dosya dizinleri (C#)](./linq-and-file-directories.md)
