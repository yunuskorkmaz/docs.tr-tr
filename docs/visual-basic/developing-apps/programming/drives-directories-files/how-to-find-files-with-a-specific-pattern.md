---
title: "Nasıl yapılır: Visual Basic'te belirli düzendeki dosyaları bulma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: e4d40c4ad3a694b3f7e830604edf94d90cb4c395
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825332"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="45b85-102">Nasıl yapılır: Visual Basic'te belirli düzendeki dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="45b85-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="45b85-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Yöntemi dosyaları için yol adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b85-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="45b85-104">Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="45b85-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="45b85-105">Alt dizinler aramaya dahil etmek istediğiniz verilirse `searchType` parametresi `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="45b85-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="45b85-106">Belirtilen desenle eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="45b85-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45b85-107">Dosya listesi kullanarak döndürme hakkında bilgi için `DirectoryInfo` sınıfının `System.IO` ad bkz <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="45b85-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="45b85-108">Belirli bir düzendeki dosyaları bulmak için</span><span class="sxs-lookup"><span data-stu-id="45b85-108">To find files with a specified pattern</span></span>  
  
-   <span data-ttu-id="45b85-109">Kullanım `GetFiles` aramak istediğiniz dizinin yolunu ve adını sağlayan ve düzeni belirtme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45b85-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="45b85-110">Aşağıdaki örnek uzantılı tüm dosyaları döndürür `.dll` dizinde eklenmeye ve `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="45b85-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="45b85-111">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="45b85-111">.NET Framework Security</span></span>  
 <span data-ttu-id="45b85-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="45b85-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="45b85-113">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="45b85-114">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="45b85-115">`directory` yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="45b85-116">`directory` Varolan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="45b85-117">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="45b85-118">Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="45b85-119">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="45b85-120">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="45b85-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b85-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45b85-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="45b85-122">Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma</span><span class="sxs-lookup"><span data-stu-id="45b85-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="45b85-123">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="45b85-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="45b85-124">Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="45b85-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
