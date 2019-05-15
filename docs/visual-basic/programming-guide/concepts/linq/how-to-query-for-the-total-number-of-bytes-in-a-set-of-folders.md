---
title: 'Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 4e69acbd42e703cdaca1d91f4597c980e6fd8508
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593275"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı
Bu örnek belirtilen bir klasördeki tüm dosyaları ve tüm alt klasörleri tarafından kullanılan bayt toplam sayısını almak nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Linq.Enumerable.Sum%2A> Yöntemi, seçilen tüm öğelerin değerini ekler `select` yan tümcesi. Belirtilen dizin ağacındaki en büyük veya en küçük dosya çağırarak almak için bu sorguyu kolayca değiştirebilirsiniz <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> yöntemi yerine <xref:System.Linq.Enumerable.Sum%2A>.  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Yalnızca belirtilen dizin ağacı bayt sayısını varsa, daha verimli bir şekilde bir veri kaynağı olarak liste koleksiyonu oluşturma işleminin ek yüke neden olur bir LINQ Sorgu oluşturmadan bunu yapabilirsiniz. Sorguyu daha karmaşık hale geldiğinde veya aynı veri kaynağında birden çok sorguları çalıştırmak sahip olduğunda LINQ yaklaşım kullanışlılığını artırır.  
  
 Sorgu dosya uzunluğu elde etmek için ayrı bir yöntemi için çağırır. Dosya başka bir iş parçacığında sonra silinmişse, oluşturulur ve olası özel kullanmak için bunu yapar <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında `GetFiles`. Olsa bile <xref:System.IO.FileInfo> nesnesi zaten oluşturuldu, özel durum ortaya çıkabilir çünkü bir <xref:System.IO.FileInfo> nesne yenilemek çalışır, <xref:System.IO.FileInfo.Length%2A> özelliği ile erişilen özelliği ilk kez en güncel uzunluğu. Bir try-catch bloğunda sorgu dışında bu işlemi koyarak kod yan etkilere neden olabilecek sorguları işlemlerinde önleme kuralı izler. Genel olarak, bir uygulama bilinmeyen bir durumda kaldı değil emin olmak için özel durumlar tükettiğinizde çok dikkatli olunmalıdır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
VB.NET konsol uygulama projesi oluşturmak bir `Imports` System.Linq ad alanı bildirimi.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects'in (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
