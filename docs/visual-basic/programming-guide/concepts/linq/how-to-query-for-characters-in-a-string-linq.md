---
title: 'Nasıl yapılır: Bir Dizedeki Karakterleri Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 2f306a488610aaa5775210eba3d7312b092545a7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345517"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="3088e-102">Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3088e-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="3088e-103"><xref:System.String> sınıfı genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini gerçekleştirdiğinden, herhangi bir dize bir karakter dizisi olarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3088e-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="3088e-104">Ancak bu, LINQ 'in yaygın bir kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="3088e-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="3088e-105">Karmaşık kalıp eşleştirme işlemleri için <xref:System.Text.RegularExpressions.Regex> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="3088e-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="3088e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3088e-106">Example</span></span>

<span data-ttu-id="3088e-107">Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemede bir dizeyi sorgular.</span><span class="sxs-lookup"><span data-stu-id="3088e-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="3088e-108">Sorgunun ilk kez yürütüldükten sonra "yeniden kullanılır" olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3088e-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="3088e-109">Sorgunun kendisi gerçek sonuçları depolamadığından bu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3088e-109">This is possible because the query itself does not store any actual results.</span></span>

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compile-the-code"></a><span data-ttu-id="3088e-110">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="3088e-110">Compile the code</span></span>

<span data-ttu-id="3088e-111">System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3088e-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="3088e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3088e-112">See also</span></span>

- [<span data-ttu-id="3088e-113">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3088e-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="3088e-114">LINQ sorgularını normal ifadelerle birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3088e-114">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)
