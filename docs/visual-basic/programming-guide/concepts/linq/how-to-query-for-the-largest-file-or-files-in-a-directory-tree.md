---
title: 'Nasıl yapılır: Bir Dizin Ağacındaki En Büyük Dosya veya Dosyalar için Sorgu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 9ae4a1442a0ecbb11d37b56302bec6a387c662aa
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078274"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="da420-102">Nasıl yapılır: bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da420-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="da420-103">Bu örnekte, bayt cinsinden dosya boyutuyla ilgili beş sorgu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="da420-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="da420-104">En büyük dosyanın bayt cinsinden boyutunu alma.</span><span class="sxs-lookup"><span data-stu-id="da420-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="da420-105">En küçük dosyanın bayt cinsinden boyutunu alma.</span><span class="sxs-lookup"><span data-stu-id="da420-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="da420-106"><xref:System.IO.FileInfo>Belirtilen kök klasörü altındaki bir veya daha fazla klasörden en büyük veya en küçük dosyayı alma.</span><span class="sxs-lookup"><span data-stu-id="da420-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="da420-107">10 en büyük dosya gibi bir sıra alma.</span><span class="sxs-lookup"><span data-stu-id="da420-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="da420-108">Dosyaları, belirli bir boyuttan daha az olan dosyaları yoksayarak, dosya boyutlarına göre gruplar halinde sıralama.</span><span class="sxs-lookup"><span data-stu-id="da420-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da420-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="da420-109">Example</span></span>  

 <span data-ttu-id="da420-110">Aşağıdaki örnek, dosya boyutlarına bağlı olarak dosyaların nasıl sorgulandığına ve gruplandıralınacağını gösteren beş ayrı sorgu içerir.</span><span class="sxs-lookup"><span data-stu-id="da420-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="da420-111">Bu örnekleri, sorgunun diğer bir özelliğindeki sorgu temel alınarak kolayca değiştirebilirsiniz <xref:System.IO.FileInfo> .</span><span class="sxs-lookup"><span data-stu-id="da420-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="da420-112">Bir veya daha fazla tamamlanmış nesne döndürmek için <xref:System.IO.FileInfo> , sorgunun her birini veri kaynağında incelemesi gerekir ve sonra bunları length özelliğinin değerine göre sıralayın.</span><span class="sxs-lookup"><span data-stu-id="da420-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="da420-113">Ardından, en büyük uzunluklara sahip tek bir veya sırası döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="da420-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="da420-114"><xref:System.Linq.Enumerable.First%2A>Bir listedeki ilk öğeyi döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="da420-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="da420-115"><xref:System.Linq.Enumerable.Take%2A>İlk n öğe sayısını döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="da420-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="da420-116">Listenin başlangıcında en küçük öğeleri yerleştirmek için azalan bir sıralama düzeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="da420-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="da420-117">Sorgu ayrı bir yönteme, dosya boyutunu bir dosyanın silindiği bir zaman diliminde başka bir iş parçacığında silinmiş olması durumunda oluşturulacak olası özel durumu tüketmek için bir kez çağırır <xref:System.IO.FileInfo> `GetFiles` .</span><span class="sxs-lookup"><span data-stu-id="da420-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="da420-118"><xref:System.IO.FileInfo>Nesne zaten oluşturulsa da, bir nesne, özelliğin <xref:System.IO.FileInfo> <xref:System.IO.FileInfo.Length%2A> ilk kez en güncel boyutunu bayt olarak yenilemeyi deneyeceğinden, özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="da420-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="da420-119">Bu işlemi sorgu dışında bir try-catch bloğuna yerleştirerek, sorguların içindeki işlemleri, yan etkilere neden olabilecek şekilde önleme kuralını izliyoruz.</span><span class="sxs-lookup"><span data-stu-id="da420-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="da420-120">Genel olarak, bir uygulamanın bilinmeyen bir durumda ayrılmadığından emin olmak için özel durumlar tüketirken harika bir dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="da420-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="da420-121">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="da420-121">Compile the code</span></span>  

<span data-ttu-id="da420-122">`Imports`System. Linq ad alanı için bir deyimle birlikte Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="da420-122">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="da420-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da420-123">See also</span></span>

- [<span data-ttu-id="da420-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da420-124">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="da420-125">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da420-125">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
