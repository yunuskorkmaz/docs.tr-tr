---
title: "Nasıl yapılır: sorgu için bir klasör (LINQ) (C#) kümesi bayt toplam sayısı"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 342ab9e23b733051679483172a1da6027f6e6f3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Nasıl yapılır: sorgu için bir klasör (LINQ) (C#) kümesi bayt toplam sayısı
Bu örnek belirtilen bir klasördeki tüm dosyaları ve onun tüm alt klasörleri tarafından kullanılan bayt toplam sayısını almak üzere nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Linq.Enumerable.Sum%2A> Yöntemi, seçilen tüm öğelerin değerini ekler `select` yan tümcesi. Belirtilen dizin ağacındaki en büyük veya en küçük dosya çağırarak almak için bu sorguyu kolayca değiştirebilirsiniz <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> yöntemi yerine <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Yalnızca belirtilen dizin ağacında bayt sayısını varsa, daha verimli bir veri kaynağı olarak liste koleksiyonu oluşturma için ek yükü doğurur LINQ Sorgu oluşturmadan bunu yapabilirsiniz. LINQ yaklaşım yararlılığı sorguyu daha karmaşık hale geldiğinde veya birden çok sorgu aynı veri kaynağına karşı çalıştırmak sahip olduğunuzda artırır.  
  
 Sorgu dosyası uzunluğu almak için ayrı bir yöntem için çağırır. Sonra başka bir iş parçacığında dosya silinirse, gerçekleştirilecektir olası özel kullanmak için bunu yapar <xref:System.IO.FileInfo> nesne çağrısında oluşturulduğu `GetFiles`. Olsa bile <xref:System.IO.FileInfo> nesnesi zaten oluşturulmuş, özel durumu oluşabilir çünkü bir <xref:System.IO.FileInfo> nesne Yenile deneyecek kendi <xref:System.IO.FileInfo.Length%2A> özelliği erişildiğinde ilk kez en son uzunluğundaki özellik. Try-catch bloğunda sorgu dışında bu işlemi koyarak kodu yan etkileri neden olan sorguları işlemlerinde önleme kuralı izler. Bir uygulama bilinmeyen bir durumda sol değil emin olmak için özel durumlar kullandığında genel olarak, çok dikkatli olunması gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
