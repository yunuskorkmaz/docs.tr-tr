---
title: 'Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 9aa098ddca2e3ad300913b207c9db5a4976eded7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831676"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="f6092-102">Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı</span><span class="sxs-lookup"><span data-stu-id="f6092-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="f6092-103">Bu örnek belirtilen bir klasördeki tüm dosyaları ve tüm alt klasörleri tarafından kullanılan bayt toplam sayısını almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6092-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6092-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6092-104">Example</span></span>  
 <span data-ttu-id="f6092-105"><xref:System.Linq.Enumerable.Sum%2A> Yöntemi, seçilen tüm öğelerin değerini ekler `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f6092-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="f6092-106">Belirtilen dizin ağacındaki en büyük veya en küçük dosya çağırarak almak için bu sorguyu kolayca değiştirebilirsiniz <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> yöntemi yerine <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6092-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="f6092-107">Yalnızca belirtilen dizin ağacı bayt sayısını varsa, daha verimli bir şekilde bir veri kaynağı olarak liste koleksiyonu oluşturma işleminin ek yüke neden olur bir LINQ Sorgu oluşturmadan bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6092-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="f6092-108">Sorguyu daha karmaşık hale geldiğinde veya aynı veri kaynağında birden çok sorguları çalıştırmak sahip olduğunda LINQ yaklaşım kullanışlılığını artırır.</span><span class="sxs-lookup"><span data-stu-id="f6092-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="f6092-109">Sorgu dosya uzunluğu elde etmek için ayrı bir yöntemi için çağırır.</span><span class="sxs-lookup"><span data-stu-id="f6092-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="f6092-110">Dosya başka bir iş parçacığında sonra silinmişse, oluşturulur ve olası özel kullanmak için bunu yapar <xref:System.IO.FileInfo> nesne oluşturulduğu çağrısında `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="f6092-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="f6092-111">Olsa bile <xref:System.IO.FileInfo> nesnesi zaten oluşturuldu, özel durum ortaya çıkabilir çünkü bir <xref:System.IO.FileInfo> nesne yenilemek çalışır, <xref:System.IO.FileInfo.Length%2A> özelliği ile erişilen özelliği ilk kez en güncel uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f6092-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="f6092-112">Bir try-catch bloğunda sorgu dışında bu işlemi koyarak kod yan etkilere neden olabilecek sorguları işlemlerinde önleme kuralı izler.</span><span class="sxs-lookup"><span data-stu-id="f6092-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="f6092-113">Genel olarak, bir uygulama bilinmeyen bir durumda kaldı değil emin olmak için özel durumlar tükettiğinizde çok dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6092-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6092-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f6092-114">Compiling the Code</span></span>  
 <span data-ttu-id="f6092-115">.NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f6092-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6092-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6092-116">See also</span></span>

- [<span data-ttu-id="f6092-117">LINQ to Objects'in (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6092-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="f6092-118">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6092-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
