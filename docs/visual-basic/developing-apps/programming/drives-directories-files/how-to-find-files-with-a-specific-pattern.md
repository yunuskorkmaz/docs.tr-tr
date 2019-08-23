---
title: 'Nasıl yapılır: Visual Basic belirli bir düzene sahip dosyaları bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: f35222d958f8b02f83c6575d940d24e359c3ae00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914725"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="4afcf-102">Nasıl yapılır: Visual Basic belirli bir düzene sahip dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="4afcf-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="4afcf-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4afcf-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="4afcf-104">Belirli bir kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4afcf-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="4afcf-105">Aramaya alt dizinler eklemek isterseniz, `searchType` parametresini olarak `SearchOption.SearchAllSubDirectories`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4afcf-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="4afcf-106">Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4afcf-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4afcf-107">`System.IO` Ad alanının `DirectoryInfo` sınıfını kullanarak bir dosya listesi döndürme hakkında daha fazla bilgi için bkz <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="4afcf-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="4afcf-108">Belirtilen bir düzene sahip dosyaları bulmak için</span><span class="sxs-lookup"><span data-stu-id="4afcf-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="4afcf-109">Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve modelini belirterek yönteminikullanın.`GetFiles`</span><span class="sxs-lookup"><span data-stu-id="4afcf-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="4afcf-110">Aşağıdaki örnek, dizininde uzantısı `.dll` olan tüm dosyaları döndürür ve içine ekler. `ListBox1`</span><span class="sxs-lookup"><span data-stu-id="4afcf-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="4afcf-111">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4afcf-111">.NET Framework Security</span></span>  
 <span data-ttu-id="4afcf-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="4afcf-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4afcf-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="4afcf-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="4afcf-114">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="4afcf-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="4afcf-115">`directory`yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4afcf-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="4afcf-116">`directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="4afcf-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="4afcf-117">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="4afcf-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="4afcf-118">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="4afcf-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="4afcf-119">Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4afcf-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="4afcf-120">Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.</span><span class="sxs-lookup"><span data-stu-id="4afcf-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afcf-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4afcf-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="4afcf-122">Nasıl yapılır: Belirli bir düzene sahip alt dizinler bulun</span><span class="sxs-lookup"><span data-stu-id="4afcf-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="4afcf-123">Sorun giderme: Metin dosyalarından okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="4afcf-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="4afcf-124">Nasıl yapılır: Dizindeki dosyaların toplanmasını al</span><span class="sxs-lookup"><span data-stu-id="4afcf-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
