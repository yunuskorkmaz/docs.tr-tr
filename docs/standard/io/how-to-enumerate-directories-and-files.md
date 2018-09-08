---
title: 'Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de83395df9e8c89a92e85b96ddd15e9f0be6ad5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207700"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="78b35-102">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="78b35-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="78b35-103">Dizinleri ve dosyaları numaralandırma bir sıralanabilir koleksiyonun adlarının dizisini döndüren yöntemler kullanarak.</span><span class="sxs-lookup"><span data-stu-id="78b35-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="78b35-104">Numaralandırılabilir bir koleksiyonunu döndüren yöntemler de kullanabilirsiniz <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="78b35-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="78b35-105">Dizin ve dosyaların büyük koleksiyonlarla çalışıyorsanız numaralandırılabilir koleksiyonları diziler daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="78b35-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="78b35-106">Bu yöntemlerden alınan numaralandırılabilir koleksiyonları sağlamak için de kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> parametresi koleksiyonun oluşturucular için sınıflar gibi <xref:System.Collections.Generic.List%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78b35-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="78b35-107">Yalnızca dizinleri ve dosyaları adlarını almak istiyorsanız, numaralandırma yöntemlerini kullanan <xref:System.IO.Directory> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78b35-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="78b35-108">Dizinleri ve dosyaları diğer özelliklerini almak istediğiniz kullanırsanız <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="78b35-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="78b35-109">Aşağıdaki tabloda, numaralandırılabilir koleksiyonları döndüren yöntemler için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="78b35-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="78b35-110">Numaralandırılacak</span><span class="sxs-lookup"><span data-stu-id="78b35-110">To enumerate</span></span>|<span data-ttu-id="78b35-111">Döndürülecek bir sıralanabilir koleksiyonun</span><span class="sxs-lookup"><span data-stu-id="78b35-111">Enumerable collection to return</span></span>|<span data-ttu-id="78b35-112">Kullanılacak yöntemi</span><span class="sxs-lookup"><span data-stu-id="78b35-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="78b35-113">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="78b35-113">Directories</span></span>|<span data-ttu-id="78b35-114">Dizin adları</span><span class="sxs-lookup"><span data-stu-id="78b35-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="78b35-115">Dizin bilgilerini (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="78b35-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78b35-116">Dosyalar</span><span class="sxs-lookup"><span data-stu-id="78b35-116">Files</span></span>|<span data-ttu-id="78b35-117">Dosya adları</span><span class="sxs-lookup"><span data-stu-id="78b35-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="78b35-118">Dosya bilgileri (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="78b35-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="78b35-119">Dosya sistemi bilgileri</span><span class="sxs-lookup"><span data-stu-id="78b35-119">File system information</span></span>|<span data-ttu-id="78b35-120">Dosya sistemi girişleri</span><span class="sxs-lookup"><span data-stu-id="78b35-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="78b35-121">Dosya sistemi bilgileri (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="78b35-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="78b35-122">Kullanarak bir üst dizin dizinlerindeki tüm dosyaları hemen numaralandırabilirsiniz rağmen <xref:System.IO.SearchOption.AllDirectories> arama seçeneği tarafından sağlanan <xref:System.IO.SearchOption> numaralandırma, yetkisiz erişim özel durumlar (<xref:System.UnauthorizedAccessException>) sabit listesine neden olabilir tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="78b35-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="78b35-123">Bu özel durumlar olası bunları catch ve ilk dizinleri numaralandırma ve ardından dosyaları numaralandırma devam edin.</span><span class="sxs-lookup"><span data-stu-id="78b35-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="78b35-124">Dizin adlarını listelemek için</span><span class="sxs-lookup"><span data-stu-id="78b35-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="78b35-125">Kullanım <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yoldaki gidemez adlarının bir listesini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="78b35-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="78b35-126">Dosya adlarında bir dizin ve alt dizinleri numaralandırma</span><span class="sxs-lookup"><span data-stu-id="78b35-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="78b35-127">Kullanım <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> bir dizin ve (isteğe bağlı) alt dizinlerinde arama yapın ve belirli bir arama deseniyle eşleşen dosya adlarının bir listesini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="78b35-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="78b35-128">DirectoryInfo nesnelerden oluşan bir koleksiyon numaralandırma</span><span class="sxs-lookup"><span data-stu-id="78b35-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="78b35-129">Kullanım <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> en üst düzey dizinler koleksiyonu almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="78b35-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="78b35-130">Tüm dizinlerde FileInfo nesnelerden oluşan bir koleksiyon numaralandırma</span><span class="sxs-lookup"><span data-stu-id="78b35-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="78b35-131">Kullanım <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> tüm dizinlerde belirtilen arama bir desenle eşleşen dosyaları koleksiyonu almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="78b35-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="78b35-132">Bu örnekte, ilk olası yetkisiz erişim özel durumları yakalamak için üst düzey dizinleri numaralandırır ve ardından dosyaları listeler.</span><span class="sxs-lookup"><span data-stu-id="78b35-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="78b35-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78b35-133">See also</span></span>

- [<span data-ttu-id="78b35-134">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="78b35-134">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
