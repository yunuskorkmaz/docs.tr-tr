---
title: 'Nasıl yapılır: Dosyaları Uzantıya Göre Gruplama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 9e0b5bc29cbfc454cc8031bcd62ed723b8995095
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344542"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="c3715-102">Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3715-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c3715-103">Bu örnek, LINQ 'ın dosya veya klasör listelerinde gelişmiş gruplandırma ve sıralama işlemleri gerçekleştirmek için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3715-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="c3715-104">Ayrıca, <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> yöntemleri kullanılarak konsol penceresinde nasıl çıkış yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3715-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3715-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3715-105">Example</span></span>  
 <span data-ttu-id="c3715-106">Aşağıdaki sorguda, belirtilen dizin ağacının içeriğini dosya adı uzantısı tarafından nasıl gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3715-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
 <span data-ttu-id="c3715-107">Bu programın çıktısı, yerel dosya sisteminin ayrıntılarına ve `startFolder` ne şekilde ayarlandığına bağlı olarak uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3715-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="c3715-108">Tüm sonuçların görüntülenmesini sağlamak için bu örnek, sonuçların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3715-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="c3715-109">Windows ve Web uygulamalarına aynı teknikler de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c3715-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="c3715-110">Kodun bir gruptaki öğelerin, iç içe geçmiş `For Each` döngüsünün gerekli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c3715-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="c3715-111">Ayrıca, listedeki geçerli konumu hesaplamak için bazı ek Logic de vardır ve kullanıcının sayfalamayı durdurmasına ve programdan çıkmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c3715-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="c3715-112">Bu durumda, disk belleği sorgusu özgün sorgudaki önbelleğe alınmış sonuçlara karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="c3715-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="c3715-113">Diğer bağlamlarda, örneğin LINQ to SQL, önbelleğe alma gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c3715-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3715-114">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="c3715-114">Compiling the Code</span></span>  
<span data-ttu-id="c3715-115">System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c3715-115">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3715-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3715-116">See also</span></span>

- [<span data-ttu-id="c3715-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3715-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="c3715-118">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3715-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
