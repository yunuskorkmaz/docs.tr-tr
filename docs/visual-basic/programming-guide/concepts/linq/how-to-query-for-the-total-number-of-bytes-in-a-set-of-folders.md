---
title: 'Nasıl yapılır: Bir Klasör Kümesindeki Toplam Bayt Sayısını Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 25e2c2894d9feccf42ee92bdddd17d8558779e6c
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266982"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Nasıl yapılır: Klasörler Kümesindeki Toplam Bayt Sayısı (LINQ) (Visual Basic) sorgusu
Bu örnek, belirtilen bir klasördeki tüm dosyalar ve tüm alt klasörleri tarafından kullanılan toplam bayt sayısını nasıl alsüreceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Yöntem, <xref:System.Linq.Enumerable.Sum%2A> `select` yan tümcede seçilen tüm öğelerin değerlerini ekler. Bu sorguyu, belirtilen dizin ağacındaki en büyük veya en küçük <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> dosyayı <xref:System.Linq.Enumerable.Sum%2A>almak için kolayca değiştirebilirsiniz.  
  
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
  
 Yalnızca belirli bir dizin ağacındaki bayt sayısını saymanız gerekiyorsa, bunu, liste koleksiyonunu veri kaynağı olarak oluşturma nın ek yüküne neden olan bir LINQ sorgusu oluşturmadan daha verimli bir şekilde yapabilirsiniz. Sorgu daha karmaşık hale geldikçe veya aynı veri kaynağına karşı birden çok sorgu çalıştırmanız gerektiğinde LINQ yaklaşımının kullanışlılığı artar.  
  
 Sorgu, dosya uzunluğunu elde etmek için ayrı bir yönteme çağırır. Bunu, <xref:System.IO.FileInfo> çağrıda nesne oluşturulduktan sonra dosya başka bir iş parçacığı üzerinde silinmişse yükseltilecek olası özel durumu tüketmek için `GetFiles`yapar. <xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine <xref:System.IO.FileInfo.Length%2A> ilk erişilen en geçerli uzunlukta yenilenmeye çalışacağından özel durum oluşabilir. Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, kod yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını izler. Genel olarak, bir uygulamanın bilinmeyen bir durumda bırakılmadığından emin olmak için özel durumları tükettiğinizde büyük özen gerekir.  
  
## <a name="compile-the-code"></a>Kodu derleme  
System.Linq ad alanı için `Imports` bir deyim içeren Visual Basic konsol uyrama projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve Dosya Dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
