---
title: 'Nasıl yapılır: Bir Klasör Kümesindeki Toplam Bayt Sayısını Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: b926a3e0ed973f449718ca5883aeabc0bfcf7b91
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347644"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Nasıl yapılır: bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (Visual Basic)
Bu örnek, belirtilen bir klasör ve tüm alt klasörlerindeki tüm dosyalar tarafından kullanılan toplam bayt sayısının nasıl alınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Linq.Enumerable.Sum%2A> yöntemi, `select` yan tümcesinde seçilen tüm öğelerin değerlerini ekler. <xref:System.Linq.Enumerable.Sum%2A>yerine <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> metodunu çağırarak, belirtilen dizin ağacındaki en büyük veya en küçük dosyayı almak için bu sorguyu kolayca değiştirebilirsiniz.  
  
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
  
 Yalnızca belirtilen bir dizin ağacındaki bayt sayısını saymanız gerekiyorsa, bunu bir veri kaynağı olarak liste koleksiyonu oluşturma ek yükünü bir LINQ sorgusu oluşturmadan daha verimli bir şekilde yapabilirsiniz. Sorgu daha karmaşık hale geldiği veya aynı veri kaynağında birden çok sorgu çalıştırmanız gerektiğinde LINQ yaklaşımın Yararlılığı artar.  
  
 Sorgu, dosya uzunluğunu elde etmek için ayrı bir yönteme çağrı yapılır. Bu, dosya başka bir iş parçacığında silinmişse, `GetFiles`çağrısında <xref:System.IO.FileInfo> nesnesi oluşturulduktan sonra oluşturulan olası özel durumu kullanmak için bunu yapar. <xref:System.IO.FileInfo> nesnesi zaten oluşturulsa da, bir <xref:System.IO.FileInfo> nesnesi, özelliğin ilk kez eriştiği <xref:System.IO.FileInfo.Length%2A> özelliğini en güncel uzunlukla yenilemeyi deneyeceğinden, özel durum oluşabilir. Bu işlemi sorgu dışında bir try-catch bloğuna koyarak, kod, yan etkilere neden olabilecek sorgularda işlemleri önleme kuralına uyar. Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar kullandığınızda harika dikkatli olunmalıdır.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
