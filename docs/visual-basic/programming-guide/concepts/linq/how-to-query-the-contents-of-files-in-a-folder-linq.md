---
title: Bir klasördeki dosyaların içeriklerini sorgulama (LINQ)
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 3ad5fd6c893d590d46be67e6320ac5b915829f4b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346042"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="a2b12-102">Bir klasördeki dosyaların içeriğini sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b12-102">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="a2b12-103">Bu örnek, belirtilen bir dizin ağacındaki tüm dosyaların üzerinde nasıl sorgu yapılacağını, her bir dosyanın nasıl açılacağını ve içeriğini incelemenizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2b12-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="a2b12-104">Bu tür bir teknik, dizin ağacı içeriğinin dizinlerini veya ters dizinlerini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2b12-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="a2b12-105">Bu örnekte basit bir dize araması gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a2b12-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="a2b12-106">Ancak, bir normal ifadeyle, daha karmaşık bir tür model eşleşmesi gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a2b12-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="a2b12-107">Daha fazla bilgi için bkz. [nasıl yapılır: LINQ sorgularını normal Ifadelerle birleştirme (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a2b12-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b12-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2b12-108">Example</span></span>  
  
```vb
Imports System.IO

Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "C:\Program Files (x86)\Microsoft Visual Studio 14.0"  

        ' Take a snapshot of the folder contents.
        Dim dir As New DirectoryInfo(startFolder)
        Dim fileList = dir.GetFiles("*.*", SearchOption.AllDirectories)

        Dim searchTerm = "Welcome"

        ' Search the contents of each file.
        ' A regular expression created with the RegEx class
        ' could be used instead of the Contains method.
        Dim queryMatchingFiles = From file In fileList _
                                 Where file.Extension = ".html" _
                                 Let fileText = GetFileText(file.FullName) _
                                 Where fileText.Contains(searchTerm) _
                                 Select file.FullName

        Console.WriteLine("The term " & searchTerm & " was found in:")

        ' Execute the query.
        For Each filename In queryMatchingFiles
            Console.WriteLine(filename)
        Next

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()

    End Sub

    ' Read the contents of the file. This is done in a separate
    ' function in order to handle potential file system errors.
    Function GetFileText(name As String) As String

        ' If the file has been deleted, the right thing
        ' to do in this case is return an empty string.
        Dim fileContents = String.Empty

        ' If the file has been deleted since we took
        ' the snapshot, ignore it and return the empty string.
        If File.Exists(name) Then
            fileContents = File.ReadAllText(name)
        End If

        Return fileContents

    End Function
End Module
```

## <a name="compile-the-code"></a><span data-ttu-id="a2b12-109">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="a2b12-109">Compile the code</span></span>

<span data-ttu-id="a2b12-110">Visual Basic konsol uygulaması projesi oluşturun, kod örneğini kopyalayıp yapıştırın ve proje özelliklerindeki başlangıç nesnesi değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a2b12-110">Create a Visual Basic console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2b12-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b12-111">See also</span></span>

- [<span data-ttu-id="a2b12-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b12-112">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="a2b12-113">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b12-113">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
