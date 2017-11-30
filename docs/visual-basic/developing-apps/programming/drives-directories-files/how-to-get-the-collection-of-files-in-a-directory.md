---
title: "Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c9245ab2593dfed5201640ecf84713582890334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="aee01-102">Nasıl Yapılır: Visual Basic'te bir Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="aee01-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="aee01-103">Aşırı <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntemi bir dizini içindeki dosyaların adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür:</span><span class="sxs-lookup"><span data-stu-id="aee01-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="aee01-104">Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> basit dosya arama alt dizinleri arama olmadan belirtilen bir dizinde için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="aee01-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="aee01-105">Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> aşırı aramanız için ek seçenekleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="aee01-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="aee01-106">Kullanabileceğiniz `wildCards` parametresini kullanarak bir arama deseni belirtin.</span><span class="sxs-lookup"><span data-stu-id="aee01-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="aee01-107">Arama alt dizinleri içerecek şekilde `searchType` parametresi <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aee01-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="aee01-108">Belirtilen desenle eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aee01-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="aee01-109">Bir dizindeki dosyaları listelemek için</span><span class="sxs-lookup"><span data-stu-id="aee01-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="aee01-110">Aşağıdakilerden birini kullanmak <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntemi aşırı yüklemeleri, içinde arama yapmak istediğiniz dizinin yolu ve adı sağladığını `directory` parametresi.</span><span class="sxs-lookup"><span data-stu-id="aee01-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="aee01-111">Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve eklenmektedir `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="aee01-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="aee01-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="aee01-112">Robust Programming</span></span>  
 <span data-ttu-id="aee01-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="aee01-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="aee01-114">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="aee01-115">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="aee01-116">`directory`yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="aee01-117">`directory`var olan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="aee01-118">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="aee01-119">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="aee01-120">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="aee01-121">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="aee01-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee01-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aee01-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [<span data-ttu-id="aee01-123">Nasıl yapılır: belirli düzendeki dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="aee01-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [<span data-ttu-id="aee01-124">Nasıl yapılır: belirli bir desendeki alt dizinleri bulma</span><span class="sxs-lookup"><span data-stu-id="aee01-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
