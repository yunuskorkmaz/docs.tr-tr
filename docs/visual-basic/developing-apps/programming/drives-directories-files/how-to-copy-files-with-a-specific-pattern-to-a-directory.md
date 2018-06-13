---
title: "Nasıl Yapılır: Visual Basic'te Belirli Düzendeki Dosyaları Dizine Kopyalama"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 6b8df24014cf809326993958472df4dae213dbab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586692"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="0e5ee-102">Nasıl Yapılır: Visual Basic'te Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="0e5ee-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="0e5ee-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Yöntemi dosyaları için yol adları temsil eden dizeleri salt okunur bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="0e5ee-104">Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="0e5ee-105">Eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="0e5ee-106">Kullanabileceğiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> yöntemi bir dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="0e5ee-107">Belirli bir düzendeki dosyaları dizine kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="0e5ee-107">To copy files with a specific pattern to a directory</span></span>  
  
1.  <span data-ttu-id="0e5ee-108">Kullanım `GetFiles` dosyaların listesini döndürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="0e5ee-109">Bu örnek belirtilen dizindeki tüm .rtf dosyaları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  <span data-ttu-id="0e5ee-110">Kullanım `CopyFile` yöntemi dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="0e5ee-111">Bu örnek dosyaları adlı dizine kopyalar `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  <span data-ttu-id="0e5ee-112">Kapat `For` deyimiyle bir `Next` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="0e5ee-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e5ee-113">Example</span></span>  
 <span data-ttu-id="0e5ee-114">Yukarıdaki kod parçacıkları tam biçiminde gösterir, aşağıdaki örnekte, tüm .rtf dosyaları belirtilen dizinde adlı dizine kopyalar `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="0e5ee-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0e5ee-115">.NET Framework Security</span></span>  
 <span data-ttu-id="0e5ee-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0e5ee-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="0e5ee-117">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="0e5ee-118">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="0e5ee-119">Dizin yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="0e5ee-120">Varolan bir dosyayı dizin işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="0e5ee-121">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="0e5ee-122">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="0e5ee-123">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="0e5ee-124">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0e5ee-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5ee-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e5ee-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [<span data-ttu-id="0e5ee-126">Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="0e5ee-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [<span data-ttu-id="0e5ee-127">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="0e5ee-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="0e5ee-128">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="0e5ee-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
