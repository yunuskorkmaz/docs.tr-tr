---
title: "Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizedeki karakter için"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ebc832763e271cc53e9c95827c301f82e9a7578a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="6b6f2-102">Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizedeki karakter için</span><span class="sxs-lookup"><span data-stu-id="6b6f2-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="6b6f2-103">Çünkü <xref:System.String> sınıfı uygulayan genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir dize bir karakter dizisi sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="6b6f2-104">Ancak, bu yaygın bir kullanımdır LINQ değildir.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="6b6f2-105">İşlem eşleştirme karmaşık desen için kullanmak <xref:System.Text.RegularExpressions.Regex> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b6f2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b6f2-106">Example</span></span>  
 <span data-ttu-id="6b6f2-107">Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemek için bir dize sorgular.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="6b6f2-108">"İlk kez yürütüldükten sonra sorguyu yeniden kullanılacağını" unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="6b6f2-109">Bu, sorgu herhangi bir gerçek sonuç depolamaz çünkü mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b6f2-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6b6f2-110">Compiling the Code</span></span>  
 <span data-ttu-id="6b6f2-111">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6f2-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b6f2-112">See Also</span></span>  
 [<span data-ttu-id="6b6f2-113">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b6f2-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="6b6f2-114">Nasıl yapılır: (Visual Basic) Normal ifadelerle LINQ sorgularını birleştirme</span><span class="sxs-lookup"><span data-stu-id="6b6f2-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
