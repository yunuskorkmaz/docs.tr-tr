---
title: 'Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma'
ms.date: 07/20/2015
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: e890900cd2f53e62a55adef56bfdb27b9787d598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643321"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma
Bu örnek, verilerin farklı kaynaklardan yeni türleri dizisi nasıl birleştirileceğini gösterir.  
  
> [!NOTE]
>  Bir veritabanı hala verilerle dosya sistemindeki bellek içi veri ya da veri katılmaya çalışmayın. Bu tür etki alanları arası birleşimler, birleştirme işlemleri veritabanı sorguları ve diğer kaynakları türleri için tanımlanabilir farklı yolları nedeniyle tanımsız sonuçlara yol açabilir. Ayrıca, veritabanındaki veri miktarını yeterince büyük ise böyle bir işlem, bellek yetersiz özel durum neden olabilecek bir risk vardır. Bellek içi veri bir veritabanından veri katılmak için ilk çağrı `ToList` veya `ToArray` veritabanında sorgu ve birleştirme döndürülen koleksiyonda gerçekleştirin.  
  
### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için  
  
-   Bölümünde açıklandığı gibi names.csv ve scores.csv dosyalarını proje klasörünüze kopyalayın [nasıl yapılır: içerik katılma öğesinden farklı dosyaları (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir adlandırılmış türü kullanmayı gösterir `Student` elektronik tablo verileri .csv biçiminde benzetimini dizeleri iki bellek içi koleksiyonundan birleştirilmiş verileri depolamak için. Dizeleri ilk koleksiyonu Öğrenci adları ve kimlikleri ve ikinci koleksiyon Öğrenci Kimliğini (ilk sütun) ve dört incelemesi puanlarını temsil eder. Yabancı anahtar olarak kullanılan kimliği.  
  
```vb  
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
        ' ExamScores member. We skip the first item in the split string   
        ' because it is the student ID, not an exam score.  
        Dim queryNamesScores = From nameLine In names  
                          Let splitName = nameLine.Split(New Char() {","})  
                          From scoreLine In scores  
                          Let splitScoreLine = scoreLine.Split(New Char() {","})  
                          Where splitName(2) = splitScoreLine(0)  
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
  
 İçinde [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md) yan tümcesi, nesne Başlatıcı her yeni örneğini oluşturmak için kullanılan `Student` iki kaynaktan verileri kullanarak nesne.  
  
 Bir sorgunun sonuçlarını depolamak yoksa anonim türler adlandırılmış türlerinden daha daha kullanışlı olabilir. Sorgu sonuçları sorgu yürütüldüğü yöntemi dışında geçirirseniz adlandırılmış türler gereklidir. Aşağıdaki örnek önceki örnekteki gibi aynı görevi gerçekleştirir, ancak yerine adlandırılmış türler anonim türler kullanır:  
  
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
    Where splitName(2) = splitScoreLine(0)  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
