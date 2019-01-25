---
title: 'Nasıl yapılır: Sıkıştırma ve çıkarma dosyaları'
ms.date: 06/06/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c35bf549dc4dcd5e12e3580c2357b64dcc42905b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650947"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="ea242-102">Nasıl yapılır: Sıkıştırma ve çıkarma dosyaları</span><span class="sxs-lookup"><span data-stu-id="ea242-102">How to: Compress and extract files</span></span>

<span data-ttu-id="ea242-103"><xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ea242-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="ea242-104">Bu türler, okumak ve sıkıştırılmış bir dosyanın içeriğini değiştirmek için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ea242-104">You can also use these types to read and modify the contents of a compressed file:</span></span>

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="ea242-105">Aşağıdaki örnekler sıkıştırılmış dosyalarıyla çalışırken gerçekleştirebileceğiniz işlevlerin bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea242-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>

## <a name="example-1---create-and-extract-a-zip-file"></a><span data-ttu-id="ea242-106">Örnek 1 - oluşturma ve bir .zip dosyasını çıkartın</span><span class="sxs-lookup"><span data-stu-id="ea242-106">Example 1 - Create and extract a .zip file</span></span>

<span data-ttu-id="ea242-107">Aşağıdaki örneği kullanarak bir .zip dosya adı uzantısına sahip sıkıştırılmış bir dosya oluşturun ve gösterilmektedir <xref:System.IO.Compression.ZipFile> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea242-107">The following example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="ea242-108">Yeni bir .zip dosyasına bir klasörün içeriğini sıkıştırır ve sonra bu içeriği yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="ea242-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="ea242-109">Kullanılacak <xref:System.IO.Compression.ZipFile> sınıfı başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.</span><span class="sxs-lookup"><span data-stu-id="ea242-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a><span data-ttu-id="ea242-110">Örnek 2 - Extract belirli dosya uzantıları</span><span class="sxs-lookup"><span data-stu-id="ea242-110">Example 2 - Extract specific file extensions</span></span>

<span data-ttu-id="ea242-111">Sonraki örnek, bir .txt uzantısına sahip dosyaları ayıklayın ve var olan bir .zip dosyasının içeriğini yineleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea242-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="ea242-112">Kullandığı <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> sıkıştırılmış dosyasındaki girişler incelemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ea242-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="ea242-113">Bir uzantı yöntemini kullanır (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) için <xref:System.IO.Compression.ZipArchiveEntry> nesne.</span><span class="sxs-lookup"><span data-stu-id="ea242-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="ea242-114">Genişletme yöntemi kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea242-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ea242-115">Kullanılacak <xref:System.IO.Compression.ZipFileExtensions> sınıfı başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.</span><span class="sxs-lookup"><span data-stu-id="ea242-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea242-116">Dosyaların sıkıştırmasını açarken, kötü amaçlı dosya yolları, bir çıkış dizini içine sıkıştırmasını istediğiniz kaçış yapılacağını da aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea242-116">When unzipping files, you must look for malicious file paths which can escape out of the directory where you want to unzip into.</span></span> <span data-ttu-id="ea242-117">Bu yol çapraz geçişi saldırısını bilinir.</span><span class="sxs-lookup"><span data-stu-id="ea242-117">This is known as a path traversal attack.</span></span>

<span data-ttu-id="ea242-118">Aşağıdaki örnek, kötü amaçlı dosya yolları için nasıl kontrol edileceğini göstermektedir ve sıkıştırmasını güvenli bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="ea242-118">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip:</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a><span data-ttu-id="ea242-119">Örnek 3 - mevcut bir .zip dosyası olarak yeni bir dosya ekleme</span><span class="sxs-lookup"><span data-stu-id="ea242-119">Example 3 - Add a new file to an existing .zip file</span></span>

<span data-ttu-id="ea242-120">Aşağıdaki örnekte <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve sıkıştırılmış dosya için yeni bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="ea242-120">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="ea242-121">Varolan bir .zip dosyasına eklediğinizde yeni dosyayı sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="ea242-121">The new file gets compressed when you add it to the existing .zip file.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a><span data-ttu-id="ea242-122">Örnek 4 - sıkıştırma ve .gz dosyaları dizini açılamadı</span><span class="sxs-lookup"><span data-stu-id="ea242-122">Example 4 - Compress and decompress a directory of .gz files</span></span>

<span data-ttu-id="ea242-123">Ayrıca <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve verileri genişletmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="ea242-123">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="ea242-124">Bunlar aynı sıkıştırma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea242-124">They use the same compression algorithm.</span></span> <span data-ttu-id="ea242-125">Sıkıştırılmış <xref:System.IO.Compression.GZipStream> .gz uzantısına sahip bir dosyaya yazılır nesneler tarafından sağlanan yöntemleri yanı sıra birçok yaygın araçları kullanarak sıkıştırması açılmış <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="ea242-125">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="ea242-126">Aşağıdaki örnek, sıkıştırma ve kullanarak bir dosya dizininde genişletmek gösterilmektedir <xref:System.IO.Compression.GZipStream> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="ea242-126">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ea242-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea242-127">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>
- [<span data-ttu-id="ea242-128">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="ea242-128">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
