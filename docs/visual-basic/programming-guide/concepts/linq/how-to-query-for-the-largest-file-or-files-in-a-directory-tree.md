---
title: 'Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: fd1ec163685af539e644d9fb4a0845fdcb3e1b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643426"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (Visual Basic)
Bu örnek, dosya boyutunu bayt cinsinden ilgili beş sorguları gösterir:  
  
-   Bayt cinsinden en büyük dosya boyutu almak nasıl.  
  
-   Bayt cinsinden en küçük dosya boyutu almak nasıl.  
  
-   Nasıl alınacağını <xref:System.IO.FileInfo> belirtilen kök klasörü altında bir veya daha fazla klasörlerden nesne büyük veya en küçük dosya.  
  
-   10 büyük dosyaları gibi bir dizi almak nasıl.  
  
-   Belirtilen bir boyuttan daha küçük olan dosyaları yoksayılıyor kendi dosya boyutunu bayt cinsinden dayanarak gruplara sipariş dosyaları nasıl.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgulama ve grup dosyaları, kendi dosya boyutunu bayt cinsinden bağlı olarak göster beş ayrı sorguları içerir. Bu örnekler diğer bazı özellikte sorguyu temel kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> nesnesi.  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Bir veya daha fazla tamamlamak döndürülecek <xref:System.IO.FileInfo> nesneleri, sorgu ilk denetleyeceğini her bir veri kaynağı ve ardından bunları kendi uzunluğu özellik değerine göre sıralama. Ardından tek tek veya ile en büyük uzunluk dizisi döndürebilir. Kullanım <xref:System.Linq.Enumerable.First%2A> listedeki ilk öğe dönün. Kullanım <xref:System.Linq.Enumerable.Take%2A> ilk n öğe sayısını döndürmek için. Listenin başında küçük öğeleri yerleştirmek için azalan sıralama düzeni belirtin.  
  
 Sorgu burada bir dosya silindi başka bir iş parçacığında bu yana sürede durumda gerçekleştirilecektir olası özel kullanmak için dosyanın bayt cinsinden boyutu almak için ayrı bir yöntem çağırır <xref:System.IO.FileInfo> nesne çağrısındaoluşturulduğu`GetFiles`. Bile aracılığıyla <xref:System.IO.FileInfo> nesnesi zaten oluşturulmuş, özel durumu oluşabilir çünkü bir <xref:System.IO.FileInfo> nesne Yenile deneyecek kendi <xref:System.IO.FileInfo.Length%2A> özelliği erişildiğinde ilk kez en güncel boyutunu bayt cinsinden kullanarak özelliği. Try-catch bloğunda sorgu dışında bu işlemi koyarak, biz yan etkileri neden olan sorguları işlemlerinde önleme kural izleyin. Genel olarak, çok dikkatli özel durumlar, kullanırken bir uygulama bilinmeyen bir durumda sol değil emin olmak için izlenmelidir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
