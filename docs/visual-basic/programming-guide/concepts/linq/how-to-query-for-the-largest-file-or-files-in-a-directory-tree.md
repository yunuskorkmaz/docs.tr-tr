---
title: 'Nasıl yapılır: Bir Dizin Ağacındaki En Büyük Dosya veya Dosyalar için Sorgu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 723a42e79f1def171a08b28986049ffa04945fc4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266995"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="4f945-102">Nasıl yapılır: Dizin Ağacındaki En Büyük Dosya veya Dosyaları Sorgula (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f945-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="4f945-103">Bu örnek, baytlarda dosya boyutuyla ilgili beş sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="4f945-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="4f945-104">En büyük dosyanın baytboyutu nasıl alınır.</span><span class="sxs-lookup"><span data-stu-id="4f945-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="4f945-105">En küçük dosyanın baytboyutu nasıl alınır.</span><span class="sxs-lookup"><span data-stu-id="4f945-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="4f945-106">Nesnenin en <xref:System.IO.FileInfo> büyük veya en küçük dosyasını belirtilen kök klasörün altındaki bir veya daha fazla klasörden alma.</span><span class="sxs-lookup"><span data-stu-id="4f945-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="4f945-107">En büyük 10 dosya gibi bir sıra nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="4f945-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="4f945-108">Belirli bir boyuttan daha az dosyaları yoksayarak, baytcinsinden dosya boyutuna göre gruplara dosya siparişi verme.</span><span class="sxs-lookup"><span data-stu-id="4f945-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f945-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f945-109">Example</span></span>  
 <span data-ttu-id="4f945-110">Aşağıdaki örnek, baytlarındaki dosya boyutlarına bağlı olarak dosyaların nasıl sorgulanır ve gruplandırılabildiğini gösteren beş ayrı sorgu içerir.</span><span class="sxs-lookup"><span data-stu-id="4f945-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="4f945-111">Sorguyu <xref:System.IO.FileInfo> nesnenin başka bir özelliğine dayandıracak şekilde bu örnekleri kolayca değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f945-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="4f945-112">Bir veya daha <xref:System.IO.FileInfo> fazla tam nesneyi döndürmek için, sorgunun önce veri kaynağındaki her birini incelemesi ve ardından uzunluk özelliğinin değerine göre sıralaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f945-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="4f945-113">Sonra tek bir veya en büyük uzunlukları ile sırasını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4f945-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="4f945-114">Listedeki ilk öğeyi döndürmek için kullanın. <xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="4f945-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="4f945-115">İlk <xref:System.Linq.Enumerable.Take%2A> n öğe sayısını döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f945-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="4f945-116">Listenin başındaki en küçük öğeleri koymak için azalan sıralama sırasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="4f945-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="4f945-117">Sorgu, <xref:System.IO.FileInfo> çağrıda nesnenin oluşturulduğu tarihten bu yana başka bir iş parçacığı üzerinde dosyanın silindiği durumda ortaya çıkacak olası özel durumu tüketmek için baytiçinde dosya boyutunu elde etmek için ayrı bir yönteme `GetFiles`çağırır.</span><span class="sxs-lookup"><span data-stu-id="4f945-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="4f945-118"><xref:System.IO.FileInfo> Nesne zaten oluşturulmuş olsa bile, bir <xref:System.IO.FileInfo> nesne özelliğine ilk erişici olduğunda baytlarda en güncel boyutu kullanarak özelliğini <xref:System.IO.FileInfo.Length%2A> yenilemeye çalışacağından özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4f945-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="4f945-119">Bu işlemi sorgunun dışındaki bir try-catch bloğuna koyarak, yan etkilere neden olabilecek sorgularda işlemlerden kaçınma kuralını uygularız.</span><span class="sxs-lookup"><span data-stu-id="4f945-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="4f945-120">Genel olarak, bir uygulamabilinmeyen bir durumda bırakılmadığından emin olmak için, özel durumlar tüketirken büyük özen gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f945-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="4f945-121">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="4f945-121">Compile the code</span></span>  
<span data-ttu-id="4f945-122">System.Linq ad alanı için `Imports` bir deyim içeren Visual Basic konsol uyrama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4f945-122">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f945-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f945-123">See also</span></span>

- [<span data-ttu-id="4f945-124">Nesnelere LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f945-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="4f945-125">LINQ ve Dosya Dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f945-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
