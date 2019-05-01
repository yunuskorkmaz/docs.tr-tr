---
title: 'Nasıl yapılır: En büyük dosya veya dizin ağacında (LINQ) (Visual Basic) dosyalar için sorgu'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 7ba330b18020b7c3b823b70d0541cdda199aa898
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008908"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Nasıl yapılır: En büyük dosya veya dizin ağacında (LINQ) (Visual Basic) dosyalar için sorgu
Bu örnek dosyanın bayt cinsinden boyutu ile ilgili beş sorguları gösterir:  
  
- Bayt cinsinden en büyük dosya boyutu almak nasıl.  
  
- En küçük dosyanın bayt cinsinden boyutunu almak nasıl.  
  
- Nasıl alınacağını <xref:System.IO.FileInfo> belirtilen kök klasörünün altında bir veya daha fazla klasörlerden nesne en büyük veya küçük dosyası.  
  
- 10 en büyük dosyaları gibi bir dizi almak nasıl.  
  
- Nasıl yapılır sırası dosyaları, dosya boyutu bayt cinsinden göre gruplara belirtilen bir boyuttan daha az olan dosyalar yoksayılıyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgulama ve bunların dosya boyutunu bayt cinsinden bağlı olarak, Grup dosyaları göster beş ayrı sorguları içerir. Bu örnekler diğer bazı özellikte sorgu temel kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> nesne.  
  
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
  
 Bir veya daha fazla tamamlamak döndürülecek <xref:System.IO.FileInfo> nesneler, sorguyu ilk denetleyeceğini her bir veri kaynağı ve sonra bunları kendi uzunluğu özelliğinin değeri sıralayın. Ardından tek bir ya da ile en fazla uzunluk dizisi döndürebilir. Kullanım <xref:System.Linq.Enumerable.First%2A> listedeki ilk öğe döndürmek için. Kullanım <xref:System.Linq.Enumerable.Take%2A> ilk n öğe sayısını döndürmek için. Listenin başında en küçük öğeleri yerleştirmek için azalan sıralama düzeni belirtin.  
  
 Burada bir dosya silindi başka bir iş parçacığında bu yana zaman dönemi içindeki durumda gerçekleştirilecektir olası özel kullanmak bayt cinsinden boyutunu almak için ayrı bir yöntem için sorguyu çağırır <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında`GetFiles`. Bile aracılığıyla <xref:System.IO.FileInfo> nesnesi zaten oluşturuldu, özel durum ortaya çıkabilir çünkü bir <xref:System.IO.FileInfo> nesne yenilemek çalışır, <xref:System.IO.FileInfo.Length%2A> erişilen özelliği ilk kez en geçerli boyutunu bayt cinsinden kullanarak özellik. Bu işlem bir try-catch bloğunda sorgu dışında koyarak, biz yan etkilere neden olabilecek sorguları işlemlerinde önleme kural izleyin. Genel olarak, çok dikkatli özel durumlar, tüketildiğinde uygulama bilinmeyen bir durumda kaldı değil emin olmak için özenli olunması gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects'in (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
