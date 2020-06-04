---
title: 'Nasıl yapılır: Dosyaları Uzantıya Göre Gruplama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 67c48cd735b51009835cbc8df3101ea3cb212a87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396551"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="3c585-102">Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c585-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="3c585-103">Bu örnek, LINQ 'ın dosya veya klasör listelerinde gelişmiş gruplandırma ve sıralama işlemleri gerçekleştirmek için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c585-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="3c585-104">Ayrıca, ve yöntemlerini kullanarak konsol penceresinde çıkışın nasıl yapılacağını gösterir <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> .</span><span class="sxs-lookup"><span data-stu-id="3c585-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c585-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c585-105">Example</span></span>  
 <span data-ttu-id="3c585-106">Aşağıdaki sorguda, belirtilen dizin ağacının içeriğini dosya adı uzantısı tarafından nasıl gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3c585-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
 <span data-ttu-id="3c585-107">Bu programın çıktısı, yerel dosya sisteminin ayrıntılarına ve ' nin ne ayarlı olduğuna bağlı olarak uzun olabilir `startFolder` .</span><span class="sxs-lookup"><span data-stu-id="3c585-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="3c585-108">Tüm sonuçların görüntülenmesini sağlamak için bu örnek, sonuçların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c585-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="3c585-109">Windows ve Web uygulamalarına aynı teknikler de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3c585-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="3c585-110">Kod, bir gruptaki öğeler, iç içe geçmiş bir döngü gerekli olduğundan emin olun `For Each` .</span><span class="sxs-lookup"><span data-stu-id="3c585-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="3c585-111">Ayrıca, listedeki geçerli konumu hesaplamak için bazı ek Logic de vardır ve kullanıcının sayfalamayı durdurmasına ve programdan çıkmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3c585-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="3c585-112">Bu durumda, disk belleği sorgusu özgün sorgudaki önbelleğe alınmış sonuçlara karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3c585-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="3c585-113">Diğer bağlamlarda, örneğin LINQ to SQL, önbelleğe alma gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3c585-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="3c585-114">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="3c585-114">Compile the code</span></span>  
<span data-ttu-id="3c585-115">`Imports`System. Linq ad alanı için bir deyimle birlikte Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3c585-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3c585-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c585-116">See also</span></span>

- [<span data-ttu-id="3c585-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c585-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="3c585-118">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c585-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
