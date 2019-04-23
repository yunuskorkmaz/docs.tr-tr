---
title: "Nasıl yapılır: Belirli bir düzendeki dosyaları Visual Basic'te bir dizine kopyalayın"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 437a7058abd9ae167fcde15d4bddbe69bc64b7e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310778"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="ed776-102">Nasıl yapılır: Belirli bir düzendeki dosyaları Visual Basic'te bir dizine kopyalayın</span><span class="sxs-lookup"><span data-stu-id="ed776-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="ed776-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Yöntemi dosyaları için yol adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed776-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="ed776-104">Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed776-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="ed776-105">Eşleşen hiçbir dosya bulunamazsa, boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ed776-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="ed776-106">Kullanabileceğiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> bir dizinine dosyalar kopyalamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed776-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="ed776-107">Belirli bir düzendeki dosyaları dizine kopyalama</span><span class="sxs-lookup"><span data-stu-id="ed776-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="ed776-108">Kullanım `GetFiles` dosyaların listesini döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed776-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="ed776-109">Bu örnek belirtilen dizindeki tüm .rtf dosyaları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed776-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="ed776-110">Kullanım `CopyFile` dosyaları kopyalamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed776-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="ed776-111">Bu örnek adlı bir dizin dosyaları kopyalar `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="ed776-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="ed776-112">Kapat `For` deyimiyle bir `Next` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ed776-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="ed776-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed776-113">Example</span></span>  
 <span data-ttu-id="ed776-114">Yukarıdaki kod, formun tamamını sunar, aşağıdaki örnekte, tüm .rtf dosyaları belirtilen dizine adlı dizine kopyalar `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="ed776-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="ed776-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ed776-115">.NET Framework Security</span></span>  
 <span data-ttu-id="ed776-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ed776-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ed776-117">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ed776-118">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="ed776-119">Dizin mevcut değil (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="ed776-120">Mevcut bir dosyayı dizine işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="ed776-121">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="ed776-122">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="ed776-123">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="ed776-124">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ed776-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed776-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed776-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="ed776-126">Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma</span><span class="sxs-lookup"><span data-stu-id="ed776-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="ed776-127">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="ed776-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="ed776-128">Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="ed776-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
