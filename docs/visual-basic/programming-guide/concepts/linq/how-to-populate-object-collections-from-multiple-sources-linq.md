---
title: "Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b52042078667ccfbefadcdf1cef5ab0873cc97b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="cc8f0-102">Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma</span><span class="sxs-lookup"><span data-stu-id="cc8f0-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="cc8f0-103">Bu örnek, verilerin farklı kaynaklardan yeni türleri dizisi nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc8f0-104">Bir veritabanı hala verilerle dosya sistemindeki bellek içi veri ya da veri katılmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-104">Do not try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="cc8f0-105">Bu tür etki alanları arası birleşimler, birleştirme işlemleri veritabanı sorguları ve diğer kaynakları türleri için tanımlanabilir farklı yolları nedeniyle tanımsız sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="cc8f0-106">Ayrıca, veritabanındaki veri miktarını yeterince büyük ise böyle bir işlem, bellek yetersiz özel durum neden olabilecek bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="cc8f0-107">Bellek içi veri bir veritabanından veri katılmak için ilk çağrı `ToList` veya `ToArray` veritabanında sorgu ve birleştirme döndürülen koleksiyonda gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="cc8f0-108">Veri dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cc8f0-108">To create the data file</span></span>  
  
-   <span data-ttu-id="cc8f0-109">Bölümünde açıklandığı gibi names.csv ve scores.csv dosyalarını proje klasörünüze kopyalayın [nasıl yapılır: içerik katılma öğesinden farklı dosyaları (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="cc8f0-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc8f0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc8f0-110">Example</span></span>  
 <span data-ttu-id="cc8f0-111">Aşağıdaki örnekte bir adlandırılmış türü kullanmayı gösterir `Student` elektronik tablo verileri .csv biçiminde benzetimini dizeleri iki bellek içi koleksiyonundan birleştirilmiş verileri depolamak için.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="cc8f0-112">Dizeleri ilk koleksiyonu Öğrenci adları ve kimlikleri ve ikinci koleksiyon Öğrenci Kimliğini (ilk sütun) ve dört incelemesi puanlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="cc8f0-113">Yabancı anahtar olarak kullanılan kimliği.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-113">The ID is used as the foreign key.</span></span>  
  
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
  
 <span data-ttu-id="cc8f0-114">İçinde [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md) yan tümcesi, nesne Başlatıcı her yeni örneğini oluşturmak için kullanılan `Student` iki kaynaktan verileri kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>  
  
 <span data-ttu-id="cc8f0-115">Bir sorgunun sonuçlarını depolamak yoksa anonim türler adlandırılmış türlerinden daha daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-115">If you do not have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="cc8f0-116">Sorgu sonuçları sorgu yürütüldüğü yöntemi dışında geçirirseniz adlandırılmış türler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="cc8f0-117">Aşağıdaki örnek önceki örnekteki gibi aynı görevi gerçekleştirir, ancak yerine adlandırılmış türler anonim türler kullanır:</span><span class="sxs-lookup"><span data-stu-id="cc8f0-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc8f0-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cc8f0-118">Compiling the Code</span></span>  
 <span data-ttu-id="cc8f0-119">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-119">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc8f0-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc8f0-120">See Also</span></span>  
 [<span data-ttu-id="cc8f0-121">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc8f0-121">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
