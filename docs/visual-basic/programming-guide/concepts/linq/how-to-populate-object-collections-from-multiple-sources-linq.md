---
title: 'Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 0228d152539abe3bf0db5a8e5bf4581eaf957b31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638827"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma

Bu örnek, yeni türleri dizisine farklı kaynaklardan verileri birleştirme gösterilmektedir.

> [!NOTE]
> Bellek içi verileri veya veri, dosya sisteminde hala bir veritabanındaki verilerle katılın çalışmayın. Böyle etki alanları arası birleştirmeler farklı şekilde, birleştirme işlemleri veritabanı sorguları ve diğer kaynağı türleri için tanımlanabilir nedeniyle tanımlanmamış sonuçlara yol açabilir. Buna ek olarak, veritabanındaki veri miktarı yeterince büyük olduğunda bu tür bir işlem bellek yetersiz özel durum neden olabilecek bir riski yoktur. Bellek içi veriler bir veritabanından veri katılmak için ilk çağrı `ToList` veya `ToArray` veritabanında sorgu ve ardından birleştirme döndürülen koleksiyon üzerinde gerçekleştirin.

## <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için

- Bölümünde anlatıldığı gibi names.csv ve scores.csv dosyaları proje klasörünüze kopyalayın [nasıl yapılır: Dosyalardan içerik (LINQ) (Visual Basic) katılın](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, adlandırılmış tür işlemi gösterilir `Student` birleştirilen verilerin elektronik tablo verilerini .csv biçiminde benzetimini dizeleri iki bellek içi koleksiyonlardan depolamak için. Dizenin ilk koleksiyon kimlikleri ve Öğrenci adlarını ve ikinci koleksiyon Öğrenci Kimliği (ilk sütunda) ve dört sınavı puanları temsil eder. Kimlik, yabancı anahtar olarak kullanılır.

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
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),
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
' The average score of Omelchenko Svetlana is 82.5
' The average score of O'Donnell Claire is 72.25
' The average score of Mortensen Sven is 84.5
' The average score of Garcia Cesar is 88.25
' The average score of Garcia Debra is 67
' The average score of Fakhouri Fadi is 92.25
' The average score of Feng Hanying is 88
' The average score of Garcia Hugo is 85.75
' The average score of Tucker Lance is 81.75
' The average score of Adams Terry is 85.25
' The average score of Zabokritski Eugene is 83
' The average score of Tucker Michael is 92
```

İçinde [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md) yan tümcesi, bir nesne Başlatıcı her yeni örneği oluşturmak için kullanılan `Student` iki kaynaklardan gelen verileri kullanarak nesne.

Bir sorgunun sonuçlarını depolamak yoksa, anonim türleri adlandırılmış türler daha kullanışlı olabilir. Sorgu sonuçları sorgunun yürütüldüğü yöntemi dışında geçirirseniz, adlandırılmış türler gereklidir. Aşağıdaki örnek önceki örnekle aynı görevi gerçekleştirir, ancak anonim türler yerine adlandırılmış türlerini kullanır:

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

## <a name="compiling-the-code"></a>Kod derleme

Oluşturun ve aşağıdaki seçeneklerden birini hedefleyen bir proje derleme:

- .NET framework sürüm 3.5 System.Core.dll öğesine başvuru ile.
- .NET framework sürüm 4.0 veya üzeri.
- .NET core sürüm 1.0 veya üzeri.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
