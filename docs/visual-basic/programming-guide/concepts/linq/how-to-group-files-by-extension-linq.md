---
title: 'Nasıl yapılır: Dosyaları Uzantıya Göre Gruplama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 3b1b02283dc65148b8a44952ce39659cc92b483a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077312"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a>Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)

Bu örnek, LINQ 'ın dosya veya klasör listelerinde gelişmiş gruplandırma ve sıralama işlemleri gerçekleştirmek için nasıl kullanılabileceğini gösterir. Ayrıca, ve yöntemlerini kullanarak konsol penceresinde çıkışın nasıl yapılacağını gösterir <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki sorguda, belirtilen dizin ağacının içeriğini dosya adı uzantısı tarafından nasıl gruplandırmak gösterilmektedir.  
  
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
  
 Bu programın çıktısı, yerel dosya sisteminin ayrıntılarına ve ' nin ne ayarlı olduğuna bağlı olarak uzun olabilir `startFolder` . Tüm sonuçların görüntülenmesini sağlamak için bu örnek, sonuçların nasıl ekleneceğini gösterir. Windows ve Web uygulamalarına aynı teknikler de uygulanabilir. Kod, bir gruptaki öğeler, iç içe geçmiş bir döngü gerekli olduğundan emin olun `For Each` . Ayrıca, listedeki geçerli konumu hesaplamak için bazı ek Logic de vardır ve kullanıcının sayfalamayı durdurmasına ve programdan çıkmasına olanak tanır. Bu durumda, disk belleği sorgusu özgün sorgudaki önbelleğe alınmış sonuçlara karşı çalıştırılır. Diğer bağlamlarda, örneğin LINQ to SQL, önbelleğe alma gerekli değildir.  
  
## <a name="compile-the-code"></a>Kodu derle  

`Imports`System. Linq ad alanı için bir deyimle birlikte Visual Basic konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
- [LINQ ve dosya dizinleri (Visual Basic)](linq-and-file-directories.md)
