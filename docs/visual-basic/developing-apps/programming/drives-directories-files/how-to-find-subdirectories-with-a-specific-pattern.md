---
title: "Nasıl yapılır: Visual Basic'te belirli bir desendeki alt dizinleri bulma"
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 705fa6e40d0e6d18826966e3f10cfd31d9e7a6ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823408"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="396f3-102">Nasıl yapılır: Visual Basic'te belirli bir desendeki alt dizinleri bulma</span><span class="sxs-lookup"><span data-stu-id="396f3-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="396f3-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Yöntemi bir dizinde bir alt dizinler için yol adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="396f3-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="396f3-104">Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="396f3-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="396f3-105">Alt dizinlerinin içeriğini aramaya dahil etmek istediğiniz verilirse `searchType` parametresi `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="396f3-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="396f3-106">Belirtilen desenle eşleşen bir dizin yok bulunamazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="396f3-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="396f3-107">Belirli bir desendeki alt dizinleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="396f3-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="396f3-108">Kullanım `GetDirectories` yöntemi, aramak istediğiniz dizinin yolunu ve adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="396f3-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="396f3-109">Aşağıdaki örnek, dizin yapısına sözcüğünü içeren tüm dizinler "Logs" adında döndürür ve eklenmeye `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="396f3-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="396f3-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="396f3-110">Robust Programming</span></span>  
 <span data-ttu-id="396f3-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="396f3-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="396f3-112">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="396f3-113">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="396f3-114">Bir veya daha fazla belirtilen joker karakter `Nothing`, boş bir dize veya yalnızca boşluk içeriyor (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="396f3-115">`directory` yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="396f3-116">`directory` Varolan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="396f3-117">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="396f3-118">Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="396f3-119">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="396f3-120">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="396f3-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396f3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="396f3-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="396f3-122">Nasıl yapılır: Belirli bir düzendeki dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="396f3-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
