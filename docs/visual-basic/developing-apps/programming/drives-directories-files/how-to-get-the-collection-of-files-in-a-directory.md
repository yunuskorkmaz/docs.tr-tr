---
title: 'Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bb07ae25b413334f94456b378f0a2339402ac668
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335331"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="40522-102">Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="40522-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="40522-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> Yöntemin aşırı yüklemeleri, bir dizindeki dosyaların adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür:</span><span class="sxs-lookup"><span data-stu-id="40522-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="40522-104">Alt dizinleri <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> aramadan, belirtilen dizinde bulunan basit bir dosya araması için aşırı yüklemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40522-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="40522-105">Aramanız için <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> ek seçenekler belirtmek üzere aşırı yüklemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40522-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="40522-106">Bir arama kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40522-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="40522-107">Aramaya alt dizinleri eklemek için `searchType` parametresini olarak <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="40522-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="40522-108">Belirtilen Düzenle eşleşen hiçbir dosya bulunamazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="40522-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="40522-109">Dizindeki dosyaları listelemek için</span><span class="sxs-lookup"><span data-stu-id="40522-109">To list files in a directory</span></span>  
  
- <span data-ttu-id="40522-110">Parametrede arama yapılacak dizinin <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> adını ve yolunu sağlayarak, yöntem aşırı yüklemelerinin birini kullanın. `directory`</span><span class="sxs-lookup"><span data-stu-id="40522-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="40522-111">Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve içine ekler `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="40522-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="40522-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="40522-112">Robust Programming</span></span>  

 <span data-ttu-id="40522-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="40522-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="40522-114">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="40522-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="40522-115">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="40522-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="40522-116">`directory`yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="40522-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="40522-117">`directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="40522-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="40522-118">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="40522-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="40522-119">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="40522-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="40522-120">Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="40522-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="40522-121">Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.</span><span class="sxs-lookup"><span data-stu-id="40522-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40522-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40522-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="40522-123">Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="40522-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="40522-124">Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="40522-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
