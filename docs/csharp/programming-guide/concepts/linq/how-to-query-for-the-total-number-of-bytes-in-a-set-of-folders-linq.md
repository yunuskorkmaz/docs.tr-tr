---
title: Klasörler kümesindeki toplam bayt sayısı (LINQ) (C#) için sorgulama
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: c6bfe6bb6d76e7ce8ea8887eef85cd64f2a025df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344825"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Klasörler kümesindeki toplam bayt sayısı (LINQ) (C#) için sorgulama
Bu örnek, belirtilen bir klasördeki tüm dosyalar ve tüm alt klasörleri tarafından kullanılan toplam bayt sayısını nasıl alsüreceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Yöntem, <xref:System.Linq.Enumerable.Sum%2A> `select` yan tümcede seçilen tüm öğelerin değerlerini ekler. Bu sorguyu, belirtilen dizin ağacındaki en büyük veya en küçük <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> dosyayı <xref:System.Linq.Enumerable.Sum%2A>almak için kolayca değiştirebilirsiniz.  
  
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
  
 Yalnızca belirli bir dizin ağacındaki bayt sayısını saymanız gerekiyorsa, bunu, liste koleksiyonunu veri kaynağı olarak oluşturma nın ek yüküne neden olan bir LINQ sorgusu oluşturmadan daha verimli bir şekilde yapabilirsiniz. Sorgu daha karmaşık hale geldikçe veya aynı veri kaynağına karşı birden çok sorgu çalıştırmanız gerektiğinde LINQ yaklaşımının kullanışlılığı artar.  
  
 Sorgu, dosya uzunluğunu elde etmek için ayrı bir yönteme çağırır. Bunu, <xref:System.IO.FileInfo> çağrıda nesne oluşturulduktan sonra dosya başka bir iş parçacığı üzerinde silinmişse yükseltilecek olası özel durumu tüketmek için `GetFiles`yapar. <xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine <xref:System.IO.FileInfo.Length%2A> ilk erişilen en geçerli uzunlukta yenilenmeye çalışacağından özel durum oluşabilir. Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, kod yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını izler. Genel olarak, bir uygulamanın bilinmeyen bir durumda bırakılmadığından emin olmak için özel durumları tükettiğinizde büyük özen gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (C#)](./linq-to-objects.md)
- [LINQ ve Dosya Dizinleri (C#)](./linq-and-file-directories.md)
