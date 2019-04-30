---
title: 'Nasıl yapılır: Sıkıştırma ve çıkarma dosyaları'
ms.date: 01/14/2019
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
ms.openlocfilehash: 9a4ea4c32f5b73b283a5982f16e55a4d078171c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752040"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="d1ee5-102">Nasıl yapılır: Sıkıştırma ve çıkarma dosyaları</span><span class="sxs-lookup"><span data-stu-id="d1ee5-102">How to: Compress and extract files</span></span>

<span data-ttu-id="d1ee5-103"><xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="d1ee5-104">Bu türler, okumak ve sıkıştırılmış bir dosyanın içeriğini değiştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="d1ee5-105">Aşağıdaki örnekler, sıkıştırılmış dosyalar ile gerçekleştirebileceğiniz işlemlerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="d1ee5-106">Örnek 1: Oluşturma ve bir .zip dosyasını çıkartın</span><span class="sxs-lookup"><span data-stu-id="d1ee5-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="d1ee5-107">Aşağıdaki örnek nasıl oluşturulacağı ve bir sıkıştırılmış ayıklamak gösterir *.zip* kullanarak dosya <xref:System.IO.Compression.ZipFile> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="d1ee5-108">Örnek bir klasörün içeriğini yeni bir sıkıştırır *.zip* dosyasını açın ve ardından zip yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span> 

<span data-ttu-id="d1ee5-109">Örneği çalıştırmak için oluşturma bir *Başlat* , program klasöründe ve ZIP dosyalarıyla doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span> 

<span data-ttu-id="d1ee5-110">"Name 'ZipFile', geçerli bağlamda yok" derleme hatası alırsanız, bir başvuru ekleyin `System.IO.Compression.FileSystem` projenize derleme.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="d1ee5-111">Örnek 2: Belirli dosya uzantılarını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="d1ee5-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="d1ee5-112">Sonraki örnekte var olan bir içindekiler yinelenir *.zip* dosyayı ve sahip dosyaları bir *.txt* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="d1ee5-113">Kullandığı <xref:System.IO.Compression.ZipArchive> zip erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> girişler incelemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="d1ee5-114">Genişletme yöntemi <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> için <xref:System.IO.Compression.ZipArchiveEntry> nesne kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> 

<span data-ttu-id="d1ee5-115">Örneği çalıştırmak için yerleştirileceği bir *.zip* adlı dosya *result.zip* program klasörünüzde.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="d1ee5-116">İstendiğinde, ayıklamak için bir klasör adı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-116">When prompted, provide a folder name to extract to.</span></span> 

<span data-ttu-id="d1ee5-117">"Name 'ZipFile', geçerli bağlamda yok" derleme hatası alırsanız, bir başvuru ekleyin `System.IO.Compression.FileSystem` projenize derleme.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="d1ee5-118">"'ZipArchive' başvurulmayan bir derlemede tanımlanan tür" hata alırsanız, bir başvuru ekleyin `System.IO.Compression` projenize derleme.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d1ee5-119">Dosyaların sıkıştırmasını açarken, çıkış dizini içine sıkıştırmasını dışında kötü amaçlı dosya yolları, aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="d1ee5-120">Bu yol çapraz geçişi saldırısını bilinir.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="d1ee5-121">Aşağıdaki örnek, kötü amaçlı dosya yolları için nasıl kontrol edileceğini göstermektedir ve sıkıştırmasını güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="d1ee5-122">Örnek 3: Bir dosya eklemek için var olan bir zip</span><span class="sxs-lookup"><span data-stu-id="d1ee5-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="d1ee5-123">Aşağıdaki örnekte <xref:System.IO.Compression.ZipArchive> varolan erişmek için sınıf *.zip* dosyası ve bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="d1ee5-124">Mevcut zip eklediğinizde yeni dosyayı sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="d1ee5-125">Örnek 4: Sıkıştırma ve .gz dosyaları açılamadı</span><span class="sxs-lookup"><span data-stu-id="d1ee5-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="d1ee5-126">Ayrıca <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve verileri genişletmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="d1ee5-127">Bunlar aynı sıkıştırma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-127">They use the same compression algorithm.</span></span> <span data-ttu-id="d1ee5-128">Sıkıştırmasını açıp <xref:System.IO.Compression.GZipStream> yazılan nesnelerin bir *.gz* birçok yaygın araçları kullanarak dosya.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="d1ee5-129">Aşağıdaki örnek, sıkıştırma ve kullanarak bir dosya dizininde genişletmek gösterilmektedir <xref:System.IO.Compression.GZipStream> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d1ee5-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d1ee5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1ee5-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="d1ee5-131">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="d1ee5-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
