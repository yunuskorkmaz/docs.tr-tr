---
title: 'Nasıl yapılır: Dizinleri ve dosyaları numaralandırma'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c751ab03875b6af89c325981c65b7bc69d0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580466"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="bb1c7-102">Nasıl yapılır: Dizinleri ve dosyaları numaralandırma</span><span class="sxs-lookup"><span data-stu-id="bb1c7-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="bb1c7-103">Dizin ve dosyaların büyük koleksiyonlarla çalışıyorsanız numaralandırılabilir koleksiyonları diziler daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="bb1c7-104">Dizinleri ve dosyaları numaralandırma için numaralandırılabilir bir dizin veya dosya adları topluluğu döndüren yöntemler kullanın veya kendi <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="bb1c7-105">Arama yapın ve yalnızca dizinleri ve dosyaları adlarını dönmek istiyorsanız, numaralandırma yöntemlerini kullanan <xref:System.IO.Directory> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="bb1c7-106">İsterseniz arama ve diğer özelliklerini dizinleri ve dosyaları iade kullanmak <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="bb1c7-107">Bu yöntemler numaralandırılabilir koleksiyonları kullanabileceğiniz <xref:System.Collections.Generic.IEnumerable%601> parametre koleksiyonu sınıfların oluşturucuları için ister <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="bb1c7-108">Dosyalar ve dizinler numaralandırılabilir koleksiyonları döndüren yöntemler aşağıdaki tabloda özetlenmiştir:</span><span class="sxs-lookup"><span data-stu-id="bb1c7-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="bb1c7-109">Arama ve döndürmek için</span><span class="sxs-lookup"><span data-stu-id="bb1c7-109">To search and return</span></span>|<span data-ttu-id="bb1c7-110">Yöntemi kullanın</span><span class="sxs-lookup"><span data-stu-id="bb1c7-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="bb1c7-111">Dizin adları</span><span class="sxs-lookup"><span data-stu-id="bb1c7-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bb1c7-112">Dizin bilgilerini (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="bb1c7-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bb1c7-113">Dosya adları</span><span class="sxs-lookup"><span data-stu-id="bb1c7-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bb1c7-114">Dosya bilgileri (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="bb1c7-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bb1c7-115">Dosya sistemi giriş adları</span><span class="sxs-lookup"><span data-stu-id="bb1c7-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bb1c7-116">Dosya sistemi giriş bilgileri (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="bb1c7-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bb1c7-117">Dizin ve dosya adları</span><span class="sxs-lookup"><span data-stu-id="bb1c7-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="bb1c7-118">Kullanarak bir üst dizin dizinlerindeki tüm dosyaları hemen numaralandırabilirsiniz rağmen <xref:System.IO.SearchOption.AllDirectories> seçeneği isteğe bağlı <xref:System.IO.SearchOption> numaralandırma <xref:System.UnauthorizedAccessException> hata yapma sabit listesi eksik.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="bb1c7-119">İlk dizinleri numaralandırma ve ardından dosyaları numaralandırma bu özel durumları yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="bb1c7-120">Örnekler: Dizin sınıfı kullanın</span><span class="sxs-lookup"><span data-stu-id="bb1c7-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="bb1c7-121">Aşağıdaki örnekte <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yolda gidemez adlarının bir listesini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="bb1c7-122">Aşağıdaki örnekte <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> yöntemi için yinelemeli olarak bir dizin ve belirli bir desenle eşleşen alt dizinlerdeki tüm dosya adlarını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="bb1c7-123">Her dosyanın her bir satır okur ve dosya adlarını ve yollarını belirtilen bir dizeyi içeren satırları gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="bb1c7-124">Örnekler: DirectoryInfo sınıfı kullanın</span><span class="sxs-lookup"><span data-stu-id="bb1c7-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="bb1c7-125">Aşağıdaki örnekte <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> yöntemi üst düzey dizinler koleksiyonu listelemek için <xref:System.IO.FileSystemInfo.CreationTimeUtc> bazı önceki <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="bb1c7-126">Aşağıdaki örnekte <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> tüm listelemek için yöntemi dosyaları <xref:System.IO.FileInfo.Length> 10 MB'ı aşıyor.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="bb1c7-127">Bu örnekte, ilk olası yetkisiz erişim özel durumları yakalamak için üst düzey dizinleri numaralandırır ve ardından dosyaları listeler.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb1c7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1c7-128">See also</span></span>

[<span data-ttu-id="bb1c7-129">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="bb1c7-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
