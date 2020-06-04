---
title: 'Nasıl yapılır: Birden Fazla Kaynaktan Nesne Koleksiyonları Doldurma (LINQ)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 9c6d8ff5165bf886d8aad87b64305819e65361ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396525"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="6b177-102">Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b177-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="6b177-103">Bu örnekte, farklı kaynaklardaki verilerin yeni türler dizisine nasıl birleştiriyapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b177-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="6b177-104">Dosya sistemindeki bellek içi verileri veya verileri, hala veritabanında bulunan verilerle birleştirmeyi denemeyin.</span><span class="sxs-lookup"><span data-stu-id="6b177-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="6b177-105">Bu tür etki alanları arası birleştirmeler, birleştirme işlemlerinin veritabanı sorguları ve diğer kaynak türleri için tanımlanabileceğinden farklı yollarla tanımsız sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="6b177-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="6b177-106">Ayrıca, veritabanındaki veri miktarı yeterince büyükse, bu tür bir işlemin bellek dışı bir özel duruma neden olabileceği bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="6b177-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="6b177-107">Verileri bir veritabanından bellek içi verilere katmak için, önce veritabanı sorgusuna çağrı yapın `ToList` `ToArray` ve ardından döndürülen koleksiyonda JOIN işlemini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="6b177-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="6b177-108">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6b177-108">To create the data file</span></span>

- <span data-ttu-id="6b177-109">Names. csv ve puanlarını. csv dosyalarını, [benzer dosyalardan (LINQ) (Visual Basic) nasıl yapılır: Içerik ekleme](how-to-join-content-from-dissimilar-files-linq.md)bölümünde açıklandığı gibi proje klasörünüze kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6b177-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b177-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b177-110">Example</span></span>

<span data-ttu-id="6b177-111">Aşağıdaki örnek, `Student` . csv biçiminde elektronik tablo verilerinin benzetimini yapan iki bellekteki iki bellek koleksiyonundan birleştirilmiş verileri depolamak için adlandırılmış bir türün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b177-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="6b177-112">İlk dize koleksiyonu, öğrenci adlarını ve kimliklerini temsil eder ve ikinci koleksiyon öğrenci KIMLIĞINI (ilk sütunda) ve dört sınav puanlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6b177-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="6b177-113">KIMLIK yabancı anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b177-113">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(1), .LastName = splitName(0), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Svetlana Omelchenko is 82.5
' The average score of Claire O'Donnell is 72.25
' The average score of Sven Mortensen is 84.5
' The average score of Cesar Garcia is 88.25
' The average score of Debra Garcia is 67
' The average score of Fadi Fakhouri is 92.25
' The average score of Hanying Feng is 88
' The average score of Hugo Garcia is 85.75
' The average score of Lance Tucker is 81.75
' The average score of Terry Adams is 85.25
' The average score of Eugene Zabokritski is 83
' The average score of Michael Tucker is 92
```

<span data-ttu-id="6b177-114">[Select yan](../../../language-reference/queries/select-clause.md) tümcesinde bir nesne Başlatıcısı, `Student` iki kaynaktaki verileri kullanarak her yeni nesnenin örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b177-114">In the [Select Clause](../../../language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="6b177-115">Bir sorgunun sonuçlarını depolamanız gerekmiyorsa, anonim türler adlandırılmış türlerden daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b177-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="6b177-116">Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin dışına geçirirseniz adlandırılmış türler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6b177-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="6b177-117">Aşağıdaki örnek, önceki örnekle aynı görevi gerçekleştirir, ancak adlandırılmış türler yerine anonim türler kullanır:</span><span class="sxs-lookup"><span data-stu-id="6b177-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="see-also"></a><span data-ttu-id="6b177-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b177-118">See also</span></span>

- [<span data-ttu-id="6b177-119">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b177-119">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
