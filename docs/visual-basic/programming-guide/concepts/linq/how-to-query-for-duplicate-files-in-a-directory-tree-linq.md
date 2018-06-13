---
title: 'Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizin ağacında yineleyen dosyalar için'
ms.date: 07/20/2015
ms.assetid: 387d7c97-95dd-4a50-9761-7e9cf8ae9e6a
ms.openlocfilehash: c9243d98c73571fcde009cddb2d5435365f20760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643192"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="ef64a-102">Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizin ağacında yineleyen dosyalar için</span><span class="sxs-lookup"><span data-stu-id="ef64a-102">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="ef64a-103">Bazen aynı ada sahip dosya birden fazla klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ef64a-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="ef64a-104">Örneğin, Visual Studio yükleme klasörü altında çeşitli klasörler Benioku.htm dosyasına sahip.</span><span class="sxs-lookup"><span data-stu-id="ef64a-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="ef64a-105">Bu örnek belirtilen kök klasörü altında böyle yinelenen dosya adları için sorgulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef64a-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="ef64a-106">Oluşturma süreleri de eşleşen ve ikinci örnek büyüklüğü dosyaları sorgulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef64a-106">The second example shows how to query for files whose size and creation times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef64a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef64a-107">Example</span></span>  
  
```vb  
Module QueryDuplicateFileNames  
  
    Public Sub Main()  
  
        Dim path As String = "C:\Program Files\Microsoft Visual Studio 9.0\Common7"  
        QueryDuplicates1(path)  
        ' Uncomment to run this query instead  
        ' QueryDuplicates2(path)  
  
    End Sub  
    Sub QueryDuplicates1(ByVal root As String)  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim duplicates = From aFile In dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories) _  
                                 Order By aFile.Name _  
                                 Group aFile By aFile.Name Into newGroup = Group _  
                                 Where newGroup.Count() >= 2 _  
                                 Select newGroup  
  
        ' Page the display so that the results can be read.  
        Dim trimLength = root.Length  
        PageOutput(duplicates, trimLength)  
  
    End Sub  
    Sub QueryDuplicates2(ByVal root As String)  
  
        ' This time a composite key is used. This sub finds all files  
        ' that have been copied into multiple subfolders.  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim duplicates = From aFile In Dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories) _  
                                 Order By aFile.Name _  
                                 Group aFile By aFile.Name, aFile.CreationTime, aFile.Length Into newGroup = Group _  
                                 Where newGroup.Count() >= 2 _  
                                 Select newGroup  
  
        ' Page the display so that the results can be read.  
        Dim trimLength = root.Length  
        PageOutput(duplicates, trimLength)  
  
    End Sub  
    ' Pages console diplay for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to diplay  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the paths in the output.  
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
  
 <span data-ttu-id="ef64a-108">İlk sorguyu basit bir anahtarı bir eşleşme belirlemek için kullanır; Bu, aynı ada sahip ancak içerikleri farklı olabilir dosyaları bulur.</span><span class="sxs-lookup"><span data-stu-id="ef64a-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="ef64a-109">İkinci sorguyu karşı üç özelliklerini eşleştirmek için bileşik bir anahtar kullanır <xref:System.IO.FileInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ef64a-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="ef64a-110">Bu sorgu aynı veya benzer içerik ve aynı ada sahip dosyaları bulmak çok daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="ef64a-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef64a-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ef64a-111">Compiling the Code</span></span>  
 <span data-ttu-id="ef64a-112">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ef64a-112">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef64a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef64a-113">See Also</span></span>  
 [<span data-ttu-id="ef64a-114">LINQ to nesneler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef64a-114">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="ef64a-115">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef64a-115">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
