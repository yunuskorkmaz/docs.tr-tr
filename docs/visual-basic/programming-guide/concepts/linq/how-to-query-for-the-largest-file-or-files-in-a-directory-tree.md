---
title: 'Nasıl yapılır: Bir Dizin Ağacındaki En Büyük Dosya veya Dosyalar için Sorgu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 34f2cd97cafbe142c9462e8d0cf7c17f9f0d16f9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346066"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Nasıl yapılır: bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (Visual Basic)
Bu örnekte, bayt cinsinden dosya boyutuyla ilgili beş sorgu gösterilmektedir:  
  
- En büyük dosyanın bayt cinsinden boyutunu alma.  
  
- En küçük dosyanın bayt cinsinden boyutunu alma.  
  
- Belirtilen kök klasörü altındaki bir veya daha fazla klasörden en büyük veya en küçük dosya <xref:System.IO.FileInfo> nesne.  
  
- 10 en büyük dosya gibi bir sıra alma.  
  
- Dosyaları, belirli bir boyuttan daha az olan dosyaları yoksayarak, dosya boyutlarına göre gruplar halinde sıralama.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya boyutlarına bağlı olarak dosyaların nasıl sorgulandığına ve gruplandıralınacağını gösteren beş ayrı sorgu içerir. Sorguyu temel alarak <xref:System.IO.FileInfo> nesnesinin diğer bir özelliğinde bu örnekleri kolayca değiştirebilirsiniz.  
  
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
  
 Bir veya daha fazla <xref:System.IO.FileInfo> nesnesi döndürmek için, sorgunun her bir veri kaynağında her birini incelemesi gerekir ve sonra bunları length özelliğinin değerine göre sıralayın. Ardından, en büyük uzunluklara sahip tek bir veya sırası döndürebilir. Bir listedeki ilk öğeyi döndürmek için <xref:System.Linq.Enumerable.First%2A> kullanın. İlk n öğe sayısını döndürmek için <xref:System.Linq.Enumerable.Take%2A> kullanın. Listenin başlangıcında en küçük öğeleri yerleştirmek için azalan bir sıralama düzeni belirtin.  
  
 Burada bir dosya silindi başka bir iş parçacığında bu yana zaman dönemi içindeki durumda gerçekleştirilecektir olası özel kullanmak bayt cinsinden boyutunu almak için ayrı bir yöntem için sorguyu çağırır <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında`GetFiles`. <xref:System.IO.FileInfo> nesne zaten oluşturulsa da, bir <xref:System.IO.FileInfo> nesnesi, özelliğin ilk kez eriştiği en güncel boyutu bayt cinsinden <xref:System.IO.FileInfo.Length%2A> yenilemeyi deneyeceğinden, özel durum ortaya çıkabilir. Bu işlemi sorgu dışında bir try-catch bloğuna yerleştirerek, sorguların içindeki işlemleri, yan etkilere neden olabilecek şekilde önleme kuralını izliyoruz. Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar tüketirken harika bir dikkatli olunması gerekir.  
  
## <a name="compile-the-code"></a>Kod derleme  
System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
