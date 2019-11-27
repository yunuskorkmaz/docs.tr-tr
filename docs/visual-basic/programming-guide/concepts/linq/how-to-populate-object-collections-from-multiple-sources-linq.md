---
title: 'Nasıl yapılır: Birden Fazla Kaynaktan Nesne Koleksiyonları Doldurma (LINQ)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 74a2a0f71e575136f1758f72f9a8db72549a9489
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346972"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (Visual Basic)

Bu örnekte, farklı kaynaklardaki verilerin yeni türler dizisine nasıl birleştiriyapılacağı gösterilmektedir.

> [!NOTE]
> Dosya sistemindeki bellek içi verileri veya verileri, hala veritabanında bulunan verilerle birleştirmeyi denemeyin. Bu tür etki alanları arası birleştirmeler, birleştirme işlemlerinin veritabanı sorguları ve diğer kaynak türleri için tanımlanabileceğinden farklı yollarla tanımsız sonuçlar verebilir. Ayrıca, veritabanındaki veri miktarı yeterince büyükse, bu tür bir işlemin bellek dışı bir özel duruma neden olabileceği bir risk vardır. Bir veritabanındaki verileri bellek içi verilere katmak için, önce veritabanı sorgusunda `ToList` veya `ToArray` çağırın ve ardından döndürülen koleksiyonda birleştirmeyi gerçekleştirin.

## <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için

- Names. csv ve puanlarını. csv dosyalarını, [benzer dosyalardan (LINQ) (Visual Basic) nasıl yapılır: Içerik ekleme](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)bölümünde açıklandığı gibi proje klasörünüze kopyalayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek,. csv biçiminde elektronik tablo verilerinin benzetimini yapan iki bellekteki iki bellek koleksiyonundan birleştirilmiş verileri depolamak için adlandırılmış bir tür `Student` nasıl kullanacağınızı gösterir. İlk dize koleksiyonu, öğrenci adlarını ve kimliklerini temsil eder ve ikinci koleksiyon öğrenci KIMLIĞINI (ilk sütunda) ve dört sınav puanlarını temsil eder. KIMLIK yabancı anahtar olarak kullanılır.

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

[Select yan](../../../../visual-basic/language-reference/queries/select-clause.md) tümcesinde bir nesne Başlatıcısı, her yeni `Student` nesnesini iki kaynaktaki verileri kullanarak oluşturmak için kullanılır.

Bir sorgunun sonuçlarını depolamanız gerekmiyorsa, anonim türler adlandırılmış türlerden daha kullanışlı olabilir. Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin dışına geçirirseniz adlandırılmış türler gereklidir. Aşağıdaki örnek, önceki örnekle aynı görevi gerçekleştirir, ancak adlandırılmış türler yerine anonim türler kullanır:

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

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
