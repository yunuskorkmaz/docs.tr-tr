---
title: "Nasıl yapılır: Visual Basic'te bir dizindeki dosya koleksiyonunu alma"
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: a0190bfdff74814c1d537c9cad6a5cb2c8dd751e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971448"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="7aa27-102">Nasıl yapılır: Visual Basic'te bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="7aa27-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="7aa27-103">Aşırı Yüklemeleri <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntem dizindeki dosyaların adlarını temsil eden dizeleri salt okunur bir koleksiyonunu döndürür:</span><span class="sxs-lookup"><span data-stu-id="7aa27-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="7aa27-104">Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> belirtilen bir dizinde arama alt dizinleri olmadan, bir basit dosya arama için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="7aa27-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="7aa27-105">Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> aramanız için ek seçenekleri belirlemek için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="7aa27-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="7aa27-106">Kullanabileceğiniz `wildCards` parametresini kullanarak arama deseni belirtin.</span><span class="sxs-lookup"><span data-stu-id="7aa27-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="7aa27-107">Alt dizinler aramaya dahil etmek için ayarlama `searchType` parametresi <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7aa27-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7aa27-108">Belirtilen desenle eşleşen hiç dosya bulunamazsa, boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7aa27-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="7aa27-109">Bir dizindeki dosyaları listelemek için</span><span class="sxs-lookup"><span data-stu-id="7aa27-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="7aa27-110">Birini <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> yöntemi aşırı yüklemeleri, içinde arama yapılacak dizinin yolunu ve adını sağlama `directory` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7aa27-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="7aa27-111">Aşağıdaki örnek, dizindeki tüm dosyaları döndürür ve eklenmeye `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="7aa27-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7aa27-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7aa27-112">Robust Programming</span></span>  
 <span data-ttu-id="7aa27-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="7aa27-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="7aa27-114">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="7aa27-115">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="7aa27-116">`directory` yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="7aa27-117">`directory` Varolan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="7aa27-118">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="7aa27-119">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="7aa27-120">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="7aa27-121">Kullanıcı gerekli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="7aa27-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa27-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aa27-122">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="7aa27-123">Nasıl yapılır: Belirli bir düzendeki dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="7aa27-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="7aa27-124">Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma</span><span class="sxs-lookup"><span data-stu-id="7aa27-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
