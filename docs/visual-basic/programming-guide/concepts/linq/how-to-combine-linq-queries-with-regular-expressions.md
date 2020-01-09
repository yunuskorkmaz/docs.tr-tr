---
title: Normal ifadelerle LINQ sorgularını birleştirme
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: a091418be1f7cc30d42a98f80ebae2d36d29b5d8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337556"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a><span data-ttu-id="a9e28-102">LINQ sorgularını normal ifadelerle birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9e28-102">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>

<span data-ttu-id="a9e28-103">Bu örnek, metin dizelerinde daha karmaşık eşleştirme için bir normal ifade oluşturmak üzere <xref:System.Text.RegularExpressions.Regex> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9e28-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="a9e28-104">LINQ sorgusu, normal ifadeyle arama yapmak istediğiniz dosyaları tam olarak filtrelemenizi ve sonuçları şekillendirmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a9e28-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>

## <a name="example"></a><span data-ttu-id="a9e28-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9e28-105">Example</span></span>

```vb
Imports System.IO
Imports System.Text.RegularExpressions

Class LinqRegExVB

    Shared Sub Main()

        ' Root folder to query, along with all subfolders.
        ' Modify this path as necessary so that it accesses your Visual Studio folder.
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"

        ' Take a snapshot of the file system.
        Dim fileList As IEnumerable(Of FileInfo) = GetFiles(startFolder)

        ' Create a regular expression to find all things "Visual".
        Dim searchTerm As New Regex("Visual (Basic|C#|C\+\+|Studio)")

        ' Search the contents of each .htm file.
        ' Remove the where clause to find even more matches!
        ' This query produces a list of files where a match
        ' was found, and a list of the matches in that file.
        ' Note: Explicit typing of "Match" in select clause.
        ' This is required because MatchCollection is not a
        ' generic IEnumerable collection.
        Dim queryMatchingFiles = From afile In fileList
                                Where afile.Extension = ".htm"
                                Let fileText = File.ReadAllText(afile.FullName)
                                Let matches = searchTerm.Matches(fileText)
                                Where (matches.Count > 0)
                                Select Name = afile.FullName,
                                       Matches = From match As Match In matches
                                                 Select match.Value

        ' Execute the query.
        Console.WriteLine("The term " & searchTerm.ToString() & " was found in:")

        For Each fileMatches In queryMatchingFiles
            ' Trim the path a bit, then write
            ' the file name in which a match was found.
            Dim s = fileMatches.Name.Substring(startFolder.Length - 1)
            Console.WriteLine(s)

            ' For this file, write out all the matching strings
            For Each match In fileMatches.Matches
                Console.WriteLine("  " + match)
            Next
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()
    End Sub

    ' Function to retrieve a list of files. Note that this is a copy
    ' of the file information.
    Shared Function GetFiles(root As String) As IEnumerable(Of FileInfo)
        Return From file In My.Computer.FileSystem.GetFiles(
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")
               Select New FileInfo(file)
    End Function

End Class
```

<span data-ttu-id="a9e28-106">Ayrıca, bir `RegEx` arama tarafından döndürülen <xref:System.Text.RegularExpressions.MatchCollection> nesnesini sorgulayabileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a9e28-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="a9e28-107">Bu örnekte, sonuçlarda yalnızca her bir eşleşmenin değeri üretilir.</span><span class="sxs-lookup"><span data-stu-id="a9e28-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="a9e28-108">Ancak, bu koleksiyonda tüm filtreleme, sıralama ve gruplama türlerini gerçekleştirmek için LINQ kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a9e28-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="a9e28-109"><xref:System.Text.RegularExpressions.MatchCollection> genel olmayan bir <xref:System.Collections.IEnumerable> koleksiyonu olduğundan, sorgudaki aralık değişkeninin türünü açıkça belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e28-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="a9e28-110">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="a9e28-110">Compile the code</span></span>

<span data-ttu-id="a9e28-111">Visual Basic konsol uygulaması projesi oluşturun, kod örneğini kopyalayıp yapıştırın ve proje özelliklerindeki başlangıç nesnesi değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a9e28-111">Create a Visual Basic console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9e28-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e28-112">See also</span></span>

- [<span data-ttu-id="a9e28-113">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9e28-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="a9e28-114">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9e28-114">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
