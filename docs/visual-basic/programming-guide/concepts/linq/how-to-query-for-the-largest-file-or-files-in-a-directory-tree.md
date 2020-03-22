---
title: 'Nasıl yapılır: Bir Dizin Ağacındaki En Büyük Dosya veya Dosyalar için Sorgu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 723a42e79f1def171a08b28986049ffa04945fc4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266995"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Nasıl yapılır: Dizin Ağacındaki En Büyük Dosya veya Dosyaları Sorgula (LINQ) (Visual Basic)
Bu örnek, baytlarda dosya boyutuyla ilgili beş sorgu gösterir:  
  
- En büyük dosyanın baytboyutu nasıl alınır.  
  
- En küçük dosyanın baytboyutu nasıl alınır.  
  
- Nesnenin en <xref:System.IO.FileInfo> büyük veya en küçük dosyasını belirtilen kök klasörün altındaki bir veya daha fazla klasörden alma.  
  
- En büyük 10 dosya gibi bir sıra nasıl alınır?  
  
- Belirli bir boyuttan daha az dosyaları yoksayarak, baytcinsinden dosya boyutuna göre gruplara dosya siparişi verme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, baytlarındaki dosya boyutlarına bağlı olarak dosyaların nasıl sorgulanır ve gruplandırılabildiğini gösteren beş ayrı sorgu içerir. Sorguyu <xref:System.IO.FileInfo> nesnenin başka bir özelliğine dayandıracak şekilde bu örnekleri kolayca değiştirebilirsiniz.  
  
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
  
 Bir veya daha <xref:System.IO.FileInfo> fazla tam nesneyi döndürmek için, sorgunun önce veri kaynağındaki her birini incelemesi ve ardından uzunluk özelliğinin değerine göre sıralaması gerekir. Sonra tek bir veya en büyük uzunlukları ile sırasını döndürebilir. Listedeki ilk öğeyi döndürmek için kullanın. <xref:System.Linq.Enumerable.First%2A> İlk <xref:System.Linq.Enumerable.Take%2A> n öğe sayısını döndürmek için kullanın. Listenin başındaki en küçük öğeleri koymak için azalan sıralama sırasını belirtin.  
  
 Sorgu, <xref:System.IO.FileInfo> çağrıda nesnenin oluşturulduğu tarihten bu yana başka bir iş parçacığı üzerinde dosyanın silindiği durumda ortaya çıkacak olası özel durumu tüketmek için baytiçinde dosya boyutunu elde etmek için ayrı bir yönteme `GetFiles`çağırır. <xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine ilk erişici olduğunda baytlarda en güncel boyutu kullanarak özelliğini <xref:System.IO.FileInfo.Length%2A> yenilemeye çalışacağından özel durum oluşabilir. Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını uygularız. Genel olarak, bir uygulamabilinmeyen bir durumda bırakılmadığından emin olmak için, özel durumlar tüketirken büyük özen gerekir.  
  
## <a name="compile-the-code"></a>Kodu derleme  
System.Linq ad alanı için `Imports` bir deyim içeren Visual Basic konsol uyrama projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve Dosya Dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
