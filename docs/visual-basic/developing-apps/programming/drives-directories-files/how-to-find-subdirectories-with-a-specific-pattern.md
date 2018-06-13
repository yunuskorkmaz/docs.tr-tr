---
title: "Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma"
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: b3c80fccea06a48c78f37dc7d1c8dcc88e143de4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586444"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="b495b-102">Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="b495b-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="b495b-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Yöntemi bir dizinde alt dizinler için yol adları temsil eden dizeleri salt okunur bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b495b-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="b495b-104">Kullanabileceğiniz `wildCards` parametresini kullanarak belirli bir desen belirtin.</span><span class="sxs-lookup"><span data-stu-id="b495b-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="b495b-105">Alt dizinlerinin içeriğini aramasına dahil etmek istiyorsanız, Ayarla `searchType` parametresi `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="b495b-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="b495b-106">Belirtilen desenle eşleşen hiç dizinleri bulunamazsa, boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b495b-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="b495b-107">Belirli bir desendeki alt dizinleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="b495b-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="b495b-108">Kullanım `GetDirectories` yöntemi, aramak istediğiniz dizin konumunu ve adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b495b-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="b495b-109">Aşağıdaki örnek, adında "Logs" sözcüğünü içeren tüm dizinleri dizin yapısına döndürür ve eklenmektedir `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="b495b-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b495b-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b495b-110">Robust Programming</span></span>  
 <span data-ttu-id="b495b-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b495b-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b495b-112">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b495b-113">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b495b-114">Bir veya daha fazla belirtilen joker karakter `Nothing`, boş bir dize veya yalnızca boşluk içeriyor (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b495b-115">`directory` yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="b495b-116">`directory` var olan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b495b-117">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b495b-118">Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="b495b-119">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="b495b-120">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="b495b-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b495b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b495b-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [<span data-ttu-id="b495b-122">Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="b495b-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
