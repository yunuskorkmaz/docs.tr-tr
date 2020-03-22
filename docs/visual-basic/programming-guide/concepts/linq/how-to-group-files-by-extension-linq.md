---
title: 'Nasıl yapılır: Dosyaları Uzantıya Göre Gruplama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 4d2c51fa62b3ec144bc5ad51b4a9f8305476645e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267034"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a>Nasıl yapılır: Uzantıya Göre Dosyaları Grupla (LINQ) (Visual Basic)
Bu örnek, LINQ'nin dosya veya klasör listelerinde gelişmiş gruplandırma ve sıralama işlemleri gerçekleştirmek için nasıl kullanılabileceğini gösterir. Ayrıca, konsol penceresinde ki çıktının nasıl <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> yöntemleri kullanılarak nasıl sayfaya çıkarı yapılacağını da gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu, belirtilen bir dizin ağacının içeriğini dosya adı uzantısına göre nasıl gruplanır şekilde gösterir.  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 Bu programdan çıktı, yerel dosya sisteminin ayrıntılarına ve ne `startFolder` için ayarlanana bağlı olarak uzun olabilir. Tüm sonuçların görüntülenmesini sağlamak için, bu örnek, sonuçlar üzerinden nasıl sayfa yapılacağını gösterir. Aynı teknikler Windows ve Web uygulamalarına da uygulanabilir. Kod, gruptaki öğeleri sayfalarından dolayı iç `For Each` içe bir döngü gerektirdiğine dikkat edin. Ayrıca, listedeki geçerli konumu hesaplamak ve kullanıcının sayfalamayı durdurup programdan çıkmasını sağlamak için bazı ek mantık da vardır. Bu özel durumda, sayfalama sorgusu özgün sorgunun önbelleğe alınmış sonuçlarına göre çalıştırılır. LINQ'dan SQL'e gibi diğer bağlamlarda, bu tür önbelleğe alma gerekmez.  
  
## <a name="compile-the-code"></a>Kodu derleme  
System.Linq ad alanı için `Imports` bir deyim içeren Visual Basic konsol uyrama projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve Dosya Dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
