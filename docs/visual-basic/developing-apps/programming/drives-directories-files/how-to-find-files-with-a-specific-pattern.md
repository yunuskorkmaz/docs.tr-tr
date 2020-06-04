---
title: 'Nasıl yapılır: Belirli bir Düzendeki Dosyaları Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 71073672ed14cb2d5df5b5365266b718c59cb18f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401647"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="0f1cc-102">Nasıl Yapılır: Visual Basic'te Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="0f1cc-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="0f1cc-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="0f1cc-104">`wildCards`Belirli bir kalıbı belirtmek için parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="0f1cc-105">Aramaya alt dizinler eklemek isterseniz, `searchType` parametresini olarak ayarlayın `SearchOption.SearchAllSubDirectories` .</span><span class="sxs-lookup"><span data-stu-id="0f1cc-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="0f1cc-106">Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f1cc-107">Ad alanının sınıfını kullanarak bir dosya listesi döndürme hakkında daha fazla bilgi için `DirectoryInfo` `System.IO` bkz <xref:System.IO.DirectoryInfo.GetFiles%2A> ..</span><span class="sxs-lookup"><span data-stu-id="0f1cc-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="0f1cc-108">Belirtilen bir düzene sahip dosyaları bulmak için</span><span class="sxs-lookup"><span data-stu-id="0f1cc-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="0f1cc-109">`GetFiles`Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve modelini belirterek yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="0f1cc-110">Aşağıdaki örnek, dizininde uzantısı olan tüm dosyaları döndürür `.dll` ve içine ekler `ListBox1` .</span><span class="sxs-lookup"><span data-stu-id="0f1cc-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="0f1cc-111">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0f1cc-111">.NET Framework Security</span></span>  

 <span data-ttu-id="0f1cc-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0f1cc-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0f1cc-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0f1cc-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0f1cc-114">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="0f1cc-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0f1cc-115">`directory`yok ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="0f1cc-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="0f1cc-116">`directory`var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="0f1cc-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0f1cc-117">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0f1cc-118">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="0f1cc-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0f1cc-119">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="0f1cc-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0f1cc-120">Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="0f1cc-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1cc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="0f1cc-122">Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="0f1cc-122">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="0f1cc-123">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="0f1cc-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="0f1cc-124">Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="0f1cc-124">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
