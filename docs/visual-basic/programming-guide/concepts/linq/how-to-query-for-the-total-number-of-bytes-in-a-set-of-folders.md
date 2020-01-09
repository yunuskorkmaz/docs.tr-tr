---
title: 'Nasıl yapılır: Bir Klasör Kümesindeki Toplam Bayt Sayısını Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c32985d7b1d87a45107159726d6ee24aea0b59b7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346034"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="70ed4-102">Nasıl yapılır: bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70ed4-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="70ed4-103">Bu örnek, belirtilen bir klasör ve tüm alt klasörlerindeki tüm dosyalar tarafından kullanılan toplam bayt sayısının nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70ed4-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70ed4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="70ed4-104">Example</span></span>  
 <span data-ttu-id="70ed4-105"><xref:System.Linq.Enumerable.Sum%2A> yöntemi, `select` yan tümcesinde seçilen tüm öğelerin değerlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="70ed4-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="70ed4-106"><xref:System.Linq.Enumerable.Sum%2A>yerine <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> metodunu çağırarak, belirtilen dizin ağacındaki en büyük veya en küçük dosyayı almak için bu sorguyu kolayca değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ed4-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="70ed4-107">Yalnızca belirtilen bir dizin ağacındaki bayt sayısını saymanız gerekiyorsa, bunu bir veri kaynağı olarak liste koleksiyonu oluşturma ek yükünü bir LINQ sorgusu oluşturmadan daha verimli bir şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ed4-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="70ed4-108">Sorgu daha karmaşık hale geldiği veya aynı veri kaynağında birden çok sorgu çalıştırmanız gerektiğinde LINQ yaklaşımın Yararlılığı artar.</span><span class="sxs-lookup"><span data-stu-id="70ed4-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="70ed4-109">Sorgu, dosya uzunluğunu elde etmek için ayrı bir yönteme çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="70ed4-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="70ed4-110">Bu, dosya başka bir iş parçacığında silinmişse, `GetFiles`çağrısında <xref:System.IO.FileInfo> nesnesi oluşturulduktan sonra oluşturulan olası özel durumu kullanmak için bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="70ed4-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="70ed4-111"><xref:System.IO.FileInfo> nesnesi zaten oluşturulsa da, bir <xref:System.IO.FileInfo> nesnesi, özelliğin ilk kez eriştiği <xref:System.IO.FileInfo.Length%2A> özelliğini en güncel uzunlukla yenilemeyi deneyeceğinden, özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="70ed4-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="70ed4-112">Bu işlemi sorgu dışında bir try-catch bloğuna koyarak, kod, yan etkilere neden olabilecek sorgularda işlemleri önleme kuralına uyar.</span><span class="sxs-lookup"><span data-stu-id="70ed4-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="70ed4-113">Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar kullandığınızda harika dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70ed4-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="70ed4-114">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="70ed4-114">Compile the code</span></span>  
<span data-ttu-id="70ed4-115">System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70ed4-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="70ed4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70ed4-116">See also</span></span>

- [<span data-ttu-id="70ed4-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70ed4-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="70ed4-118">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70ed4-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
