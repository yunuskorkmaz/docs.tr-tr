---
title: "Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: caf9bdec017a5466269ff7fe97be4d0243035b4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="84cc0-102">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="84cc0-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="84cc0-103">Dizeleri adlarının numaralandırılabilir bir koleksiyonu döndüren yöntemler kullanarak dizinleri ve dosyaları numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="84cc0-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="84cc0-104">Numaralandırılabilir bir koleksiyonu döndüren yöntemler de kullanabilirsiniz <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="84cc0-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="84cc0-105">Dizin ve dosyaların büyük koleksiyonlarla çalışırken numaralandırılabilir koleksiyonları diziler daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="84cc0-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="84cc0-106">Sağlamak için bu yöntemlerden elde numaralandırılabilir koleksiyonları kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> parametresi koleksiyonunun oluşturucuları için sınıflar gibi <xref:System.Collections.Generic.List%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="84cc0-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="84cc0-107">Yalnızca dizinleri ve dosyaları adlarını almak istiyorsanız, numaralandırma yöntemlerini kullanın <xref:System.IO.Directory> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="84cc0-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="84cc0-108">Dizinleri ve dosyaları diğer özelliklerini edinmek istiyorsanız, kullanmak <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="84cc0-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="84cc0-109">Aşağıdaki tabloda numaralandırılabilir koleksiyonları döndüren yöntemler için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="84cc0-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="84cc0-110">Numaralandırılacak</span><span class="sxs-lookup"><span data-stu-id="84cc0-110">To enumerate</span></span>|<span data-ttu-id="84cc0-111">Döndürülecek numaralandırılabilir koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="84cc0-111">Enumerable collection to return</span></span>|<span data-ttu-id="84cc0-112">Kullanılacak yöntemi</span><span class="sxs-lookup"><span data-stu-id="84cc0-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="84cc0-113">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="84cc0-113">Directories</span></span>|<span data-ttu-id="84cc0-114">Dizin adları</span><span class="sxs-lookup"><span data-stu-id="84cc0-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="84cc0-115">Dizin bilgileri (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="84cc0-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc0-116">Dosyalar</span><span class="sxs-lookup"><span data-stu-id="84cc0-116">Files</span></span>|<span data-ttu-id="84cc0-117">Dosya adları</span><span class="sxs-lookup"><span data-stu-id="84cc0-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="84cc0-118">Dosya bilgileri (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="84cc0-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84cc0-119">Dosya sistemi bilgileri</span><span class="sxs-lookup"><span data-stu-id="84cc0-119">File system information</span></span>|<span data-ttu-id="84cc0-120">Dosya sistemi girişleri</span><span class="sxs-lookup"><span data-stu-id="84cc0-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="84cc0-121">Dosya sistemi bilgileri (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="84cc0-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="84cc0-122">Kullanarak bir üst dizine dizinlerindeki tüm dosyaları hemen numaralandırabilir rağmen <xref:System.IO.SearchOption.AllDirectories> arama seçeneği tarafından sağlanan <xref:System.IO.SearchOption> numaralandırma, yetkisiz erişim özel durumları (<xref:System.UnauthorizedAccessException>) numaralandırma neden olabilir tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="84cc0-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="84cc0-123">Bu özel durumlar olası varsa, bunları catch ve ilk dizinleri numaralandırma ve dosyaları numaralandırma devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84cc0-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="84cc0-124">Dizin adlarını numaralandırılamıyor</span><span class="sxs-lookup"><span data-stu-id="84cc0-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="84cc0-125">Kullanım <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yoldaki üst düzey dizin adlarının bir listesini elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84cc0-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="84cc0-126">Dosya adları bir dizin ve alt dizinlerinde numaralandırılamıyor</span><span class="sxs-lookup"><span data-stu-id="84cc0-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="84cc0-127">Kullanım <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> yöntemi bir dizin ve (isteğe bağlı) dizinlerinden aramak ve belirtilen arama deseniyle eşleşen dosya adlarının bir listesini almak için.</span><span class="sxs-lookup"><span data-stu-id="84cc0-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="84cc0-128">DirectoryInfo nesneler koleksiyonunu numaralandırılamıyor</span><span class="sxs-lookup"><span data-stu-id="84cc0-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="84cc0-129">Kullanım <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> en üst düzey dizinler koleksiyonu elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84cc0-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="84cc0-130">Tüm dizinlerde FileInfo nesneler koleksiyonunu numaralandırılamıyor</span><span class="sxs-lookup"><span data-stu-id="84cc0-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="84cc0-131">Kullanım <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> tüm dizinlerde belirtilen arama deseniyle eşleşen dosya koleksiyonunu elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84cc0-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="84cc0-132">Bu örnekte, ilk olası yetkisiz erişim özel durumları yakalamak için üst düzey dizinler numaralandırır ve dosyaları sıralar.</span><span class="sxs-lookup"><span data-stu-id="84cc0-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="84cc0-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84cc0-133">See Also</span></span>  
 [<span data-ttu-id="84cc0-134">Dosya ve akış t-O</span><span class="sxs-lookup"><span data-stu-id="84cc0-134">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
