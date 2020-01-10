---
title: 'Nasıl yapılır: dizinleri ve dosyaları numaralandırma'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707751"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="f5e8d-102">Nasıl yapılır: dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="f5e8d-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="f5e8d-103">Sıralanabilir koleksiyonlar, büyük dizin ve dosya koleksiyonlarıyla çalışırken dizilerden daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="f5e8d-104">Dizinleri ve dosyaları numaralandırmak için dizin veya dosya adlarının veya <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>veya <xref:System.IO.FileSystemInfo> nesnelerinin sıralanabilir bir koleksiyonunu döndüren yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="f5e8d-105">Yalnızca dizinlerin veya dosyaların adlarını aramak ve döndürmek istiyorsanız, <xref:System.IO.Directory> sınıfının numaralandırma yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="f5e8d-106">Dizinlerin veya dosyaların diğer özelliklerini aramak ve döndürmek istiyorsanız <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="f5e8d-107">Bu yöntemlerdeki sıralanabilir koleksiyonları, <xref:System.Collections.Generic.List%601>gibi koleksiyon sınıflarının oluşturucuları için <xref:System.Collections.Generic.IEnumerable%601> parametresi olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="f5e8d-108">Aşağıdaki tabloda, dosya ve dizinlerin numaralandırılabilir koleksiyonlarını döndüren yöntemler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="f5e8d-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="f5e8d-109">Aramak ve döndürmek için</span><span class="sxs-lookup"><span data-stu-id="f5e8d-109">To search and return</span></span>|<span data-ttu-id="f5e8d-110">Use yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5e8d-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="f5e8d-111">Dizin adları</span><span class="sxs-lookup"><span data-stu-id="f5e8d-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5e8d-112">Dizin bilgileri (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="f5e8d-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5e8d-113">Dosya adları</span><span class="sxs-lookup"><span data-stu-id="f5e8d-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5e8d-114">Dosya bilgileri (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="f5e8d-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5e8d-115">Dosya sistemi giriş adları</span><span class="sxs-lookup"><span data-stu-id="f5e8d-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5e8d-116">Dosya sistemi giriş bilgileri (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="f5e8d-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5e8d-117">Dizin ve dosya adları</span><span class="sxs-lookup"><span data-stu-id="f5e8d-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="f5e8d-118">İsteğe bağlı <xref:System.IO.SearchOption> sabit listesinin <xref:System.IO.SearchOption.AllDirectories> seçeneğini kullanarak bir üst dizinin alt dizinlerindeki tüm dosyaları hemen numaralandırabilirsiniz, ancak <xref:System.UnauthorizedAccessException> hatalar numaralandırmayı tamamlanmamış hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="f5e8d-119">Önce dizinleri listeleyerek ve sonra dosyaları numaralandırarak bu özel durumları yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="f5e8d-120">Örnekler: Dizin sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="f5e8d-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="f5e8d-121">Aşağıdaki örnek, belirtilen yoldaki en üst düzey dizin adlarının listesini almak için <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="f5e8d-122">Aşağıdaki örnek, belirli bir kalıpla eşleşen bir dizin ve alt dizinler içindeki tüm dosya adlarını yinelemeli olarak numaralandırmak için <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="f5e8d-123">Sonra her bir dosyanın her bir satırını okur ve belirtilen bir dizeyi içeren satırları dosya adlarıyla ve yollarıyla görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="f5e8d-124">Örnekler: DirectoryInfo sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="f5e8d-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="f5e8d-125">Aşağıdaki örnek, <xref:System.IO.FileSystemInfo.CreationTimeUtc> belirli bir <xref:System.DateTime> değerinden daha eski olan en üst düzey dizinlerin bir koleksiyonunu listelemek için <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="f5e8d-126">Aşağıdaki örnek, <xref:System.IO.FileInfo.Length> 10 MB 'ı aşan tüm dosyaları listelemek için <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="f5e8d-127">Bu örnek öncelikle, olası yetkisiz erişim özel durumlarını yakalamak ve sonra dosyaları numaralandırmaları için üst düzey dizinleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f5e8d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e8d-128">See also</span></span>

- [<span data-ttu-id="f5e8d-129">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="f5e8d-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
