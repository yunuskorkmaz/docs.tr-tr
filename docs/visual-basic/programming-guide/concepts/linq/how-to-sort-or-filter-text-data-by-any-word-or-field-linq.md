---
title: 'Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) (Visual Basic) göre filtre metin verilerini sıralama veya'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 46c9149a7cb1809bf94162649de0a35110bbc697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294515"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="d4212-102">Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) (Visual Basic) göre filtre metin verilerini sıralama veya</span><span class="sxs-lookup"><span data-stu-id="d4212-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="d4212-103">Aşağıdaki örnek nasıl satırında herhangi bir alan olarak virgülle ayrılmış değerler gibi yapılandırılmış metin satırlarını sıralanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4212-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="d4212-104">Alanın, çalışma zamanında dinamik olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4212-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="d4212-105">Scores.csv alanlarında dört test puanlarını bir dizi tarafından izlenen bir öğrenci kimlik numarasını temsil ettiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="d4212-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="d4212-106">Veri içeren bir dosya oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d4212-106">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="d4212-107">Konu başlığından scores.csv veri kopyalama [nasıl yapılır: İçerik gelen benzer olmayan dosyaları (LINQ) (Visual Basic) katılın](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) ve Çözüm klasörünüz olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d4212-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4212-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4212-108">Example</span></span>  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 <span data-ttu-id="d4212-109">Bu örnek ayrıca sorgu değişkeni bir işlevden döndürülecek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4212-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d4212-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d4212-110">Compiling the Code</span></span>  
 <span data-ttu-id="d4212-111">.NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="d4212-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4212-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4212-112">See also</span></span>

- [<span data-ttu-id="d4212-113">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4212-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
