---
title: 'Nasıl Yapılır: Gruplar Kullanarak Bir Dosyayı Birden Çok Dosyaya Bölme (LINQ)'
ms.date: 07/20/2015
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
ms.openlocfilehash: 07d53c9afca88cd3156c7fc8fcfab5ac7ca24f25
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348036"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a><span data-ttu-id="1b1f4-102">Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b1f4-102">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="1b1f4-103">Bu örnek, iki dosyanın içeriğini birleştirmenin bir yolunu gösterir ve ardından verileri yeni bir şekilde düzenleyen yeni bir dosya kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b1f4-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>

### <a name="to-create-the-data-files"></a><span data-ttu-id="1b1f4-104">Veri dosyalarını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b1f4-104">To create the data files</span></span>

1. <span data-ttu-id="1b1f4-105">Bu adları names1. txt adlı bir metin dosyasına kopyalayın ve proje klasörünüze kaydedin:</span><span class="sxs-lookup"><span data-stu-id="1b1f4-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>

    ```text
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Potra, Cristina
    Noriega, Fabricio
    Aw, Kam Foo
    Beebe, Ann
    Toyoshima, Tim
    Guy, Wey Yuan
    Garcia, Debra
    ```

2. <span data-ttu-id="1b1f4-106">Bu adları names2. txt adlı bir metin dosyasına kopyalayın ve proje klasörünüze kaydedin: iki dosyanın ortak olarak bazı adlara sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1b1f4-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>

    ```text
    Liu, Jinghao
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Beebe, Ann
    Gilchrist, Beth
    Myrcha, Jacek
    Giakoumakis, Leo
    McLin, Nkenge
    El Yassir, Mehdi
    ```

## <a name="example"></a><span data-ttu-id="1b1f4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b1f4-107">Example</span></span>

```vb
Class SplitWithGroups

    Shared Sub Main()

        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")

        ' Concatenate and remove duplicate names based on
        Dim mergeQuery As IEnumerable(Of String) = fileA.Union(fileB)

        ' Group the names by the first letter in the last name
        Dim groupQuery = From name In mergeQuery
                     Let n = name.Split(New Char() {","})
                     Order By n(0)
                     Group By groupKey = n(0)(0)
                     Into groupName = Group

        ' Create a new file for each group that was created
        ' Note that nested foreach loops are required to access
        ' individual items with each group.
        For Each gGroup In groupQuery
            Dim fileName As String = "..'..'..'testFile_" & gGroup.groupKey & ".txt"
            Dim sw As New System.IO.StreamWriter(fileName)
            Console.WriteLine(gGroup.groupKey)
            For Each item In gGroup.groupName
                Console.WriteLine("   " & item.name)
                sw.WriteLine(item.name)
            Next
            sw.Close()
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Files have been written. Press any key to exit.")
        Console.ReadKey()

    End Sub
End Class
' Console Output:
' A
'    Aw, Kam Foo
' B
'    Bankov, Peter
'    Beebe, Ann
' E
'    El Yassir, Mehdi
' G
'    Garcia, Hugo
'    Garcia, Debra
'    Giakoumakis, Leo
'    Gilchrist, Beth
'    Guy, Wey Yuan
' H
'    Holm, Michael
' L
'    Liu, Jinghao
' M
'    McLin, Nkenge
'    Myrcha, Jacek
' N
'    Noriega, Fabricio
' P
'    Potra, Cristina
' T
'    Toyoshima, Tim
```

<span data-ttu-id="1b1f4-108">Program, veri dosyalarıyla aynı klasöre her bir grup için ayrı bir dosya yazar.</span><span class="sxs-lookup"><span data-stu-id="1b1f4-108">The program writes a separate file for each group in the same folder as the data files.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="1b1f4-109">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="1b1f4-109">Compile the code</span></span>

<span data-ttu-id="1b1f4-110">System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b1f4-110">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b1f4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b1f4-111">See also</span></span>

- [<span data-ttu-id="1b1f4-112">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b1f4-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="1b1f4-113">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b1f4-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
