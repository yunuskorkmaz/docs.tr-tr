---
title: 'Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348753"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="f640d-102">Nasıl Yapılır: Visual Basic'te Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="f640d-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="f640d-103">Yöntem, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> dosyaların yol adlarını temsil eden salt okunur dizeler koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f640d-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="f640d-104">`wildCards` Belirli bir desen belirtmek için parametrekullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f640d-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="f640d-105">Alt dizinleri aramaya eklemek istiyorsanız, parametreyi `searchType` ' `SearchOption.SearchAllSubDirectories`ye ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="f640d-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="f640d-106">Belirtilen desenle eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f640d-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f640d-107">Ad `DirectoryInfo` alanının sınıfını kullanarak dosya listesini döndürme hakkında bilgi için bkz. <xref:System.IO.DirectoryInfo.GetFiles%2A> `System.IO`</span><span class="sxs-lookup"><span data-stu-id="f640d-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="f640d-108">Belirli bir desene sahip dosyaları bulmak için</span><span class="sxs-lookup"><span data-stu-id="f640d-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="f640d-109">Arama `GetFiles` yapmak istediğiniz dizinin adını ve yolunu sağlayarak ve deseni belirterek yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f640d-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="f640d-110">Aşağıdaki örnek, dizindeki uzantılı `.dll` tüm dosyaları döndürür ve `ListBox1`ekler.</span><span class="sxs-lookup"><span data-stu-id="f640d-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="f640d-111">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f640d-111">.NET Framework Security</span></span>  

 <span data-ttu-id="f640d-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f640d-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f640d-113">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f640d-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="f640d-114">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="f640d-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="f640d-115">`directory`yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f640d-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="f640d-116">`directory`varolan bir dosyaya işaret eder (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f640d-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f640d-117">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="f640d-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f640d-118">Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="f640d-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="f640d-119">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="f640d-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="f640d-120">Kullanıcı gerekli izinleri yoksun<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="f640d-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f640d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f640d-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="f640d-122">Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="f640d-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="f640d-123">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="f640d-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="f640d-124">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="f640d-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
