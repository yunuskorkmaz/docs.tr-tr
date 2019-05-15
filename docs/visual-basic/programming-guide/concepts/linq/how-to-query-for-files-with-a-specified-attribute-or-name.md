---
title: 'Nasıl yapılır: Belirli bir öznitelik veya ada (Visual Basic) sahip dosyaları sorgulama'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 05dfe3e88274efe8d817defcac2f47efe053b12b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586491"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="fefca-102">Nasıl yapılır: Belirli bir öznitelik veya ada (Visual Basic) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="fefca-102">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>
<span data-ttu-id="fefca-103">Bu örnek nasıl (örneğin, ".txt") belirtilen dosya adı uzantısına sahip tüm dosyaları bulmak belirtilen dizin ağacında gösterir.</span><span class="sxs-lookup"><span data-stu-id="fefca-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="fefca-104">Ayrıca oluşturma saatini temel alan ağacında ya da yeni veya eski dosyayı iade işlemini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="fefca-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fefca-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fefca-105">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fefca-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fefca-106">Compiling the Code</span></span>  
<span data-ttu-id="fefca-107">VB.NET konsol uygulama projesi oluşturmak bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="fefca-107">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fefca-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fefca-108">See also</span></span>

- [<span data-ttu-id="fefca-109">LINQ to Objects'in (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fefca-109">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="fefca-110">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fefca-110">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
