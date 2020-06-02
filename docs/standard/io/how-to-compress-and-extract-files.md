---
title: 'Nasıl yapılır: dosyaları sıkıştırma ve ayıklama'
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
ms.openlocfilehash: 28f9a0baa73f58b0a5c7f93a4b0b3ece3b87c3a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288569"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="1147c-102">Nasıl yapılır: dosyaları sıkıştırma ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="1147c-102">How to: Compress and extract files</span></span>

<span data-ttu-id="1147c-103"><xref:System.IO.Compression>Ad alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmayı açma için aşağıdaki türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1147c-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="1147c-104">Bu türleri, sıkıştırılmış bir dosyanın içeriğini okumak ve değiştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1147c-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="1147c-105">Aşağıdaki örneklerde, sıkıştırılmış dosyalarla gerçekleştirebileceğiniz bazı işlemler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1147c-105">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="1147c-106">Bu örnekler, projenize aşağıdaki NuGet paketlerinin eklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1147c-106">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="1147c-107">System. ıO. Compression</span><span class="sxs-lookup"><span data-stu-id="1147c-107">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="1147c-108">System. ıO. Compression. ZipFile</span><span class="sxs-lookup"><span data-stu-id="1147c-108">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="1147c-109">.NET Framework kullanıyorsanız, projenize bu iki kitaplıklara başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1147c-109">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="1147c-110">Örnek 1: bir. zip dosyası oluşturma ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="1147c-110">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="1147c-111">Aşağıdaki örnek, sınıfını kullanarak sıkıştırılmış bir *. zip* dosyası oluşturmayı ve ayıklamayı gösterir <xref:System.IO.Compression.ZipFile> .</span><span class="sxs-lookup"><span data-stu-id="1147c-111">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="1147c-112">Örnek, bir klasörün içeriğini yeni bir *. zip* dosyasına sıkıştırır ve sonra zip 'i yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1147c-112">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="1147c-113">Örneği çalıştırmak için, program klasörünüzde bir *Başlangıç* klasörü oluşturun ve dosyaları ZIP 'e göre doldurun.</span><span class="sxs-lookup"><span data-stu-id="1147c-113">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="1147c-114">Örnek 2: belirli dosya uzantılarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="1147c-114">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="1147c-115">Sonraki örnek, var olan bir *. zip* dosyasının içeriği boyunca yinelenir ve *. txt* uzantısına sahip dosyaları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1147c-115">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="1147c-116"><xref:System.IO.Compression.ZipArchive>ZIP 'e erişmek için sınıfını ve <xref:System.IO.Compression.ZipArchiveEntry> tek tek girişleri incelemek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1147c-116">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="1147c-117">Nesnesinin genişletme yöntemi <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> <xref:System.IO.Compression.ZipArchiveEntry> <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1147c-117">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="1147c-118">Örneği çalıştırmak için program klasörünüze *Result. zip* adlı bir *. zip* dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1147c-118">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="1147c-119">İstendiğinde, ' a Ayıklanacak bir klasör adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1147c-119">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1147c-120">Dosyaları kaldırdığınızda, geri yüklediğiniz dizinden çıkmak için kötü amaçlı dosya yolları araması yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1147c-120">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="1147c-121">Bu, yol çapraz geçişi saldırısı olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="1147c-121">This is known as a path traversal attack.</span></span> <span data-ttu-id="1147c-122">Aşağıdaki örnek, kötü amaçlı dosya yollarının nasıl denetleyeceğinizi ve sıkıştırmayı açmak için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1147c-122">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="1147c-123">Örnek 3: mevcut bir zip dosyasına dosya ekleme</span><span class="sxs-lookup"><span data-stu-id="1147c-123">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="1147c-124">Aşağıdaki örnek, <xref:System.IO.Compression.ZipArchive> sınıfını var olan bir *. zip* dosyasına erişmek için kullanır ve buna bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="1147c-124">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="1147c-125">Yeni dosya, var olan zip 'e eklediğinizde sıkıştırılır.</span><span class="sxs-lookup"><span data-stu-id="1147c-125">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="1147c-126">Örnek 4:. gz dosyalarını sıkıştır ve aç</span><span class="sxs-lookup"><span data-stu-id="1147c-126">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="1147c-127">Ayrıca, <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> verileri sıkıştırmak ve açmak için ve sınıflarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1147c-127">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="1147c-128">Aynı sıkıştırma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1147c-128">They use the same compression algorithm.</span></span> <span data-ttu-id="1147c-129"><xref:System.IO.Compression.GZipStream>Birçok ortak araç kullanarak bir *. gz* dosyasına yazılmış nesneleri açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1147c-129">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="1147c-130">Aşağıdaki örnek, sınıfını kullanarak bir dosya dizinini nasıl sıkıştırmak ve açmak gösterilmektedir <xref:System.IO.Compression.GZipStream> :</span><span class="sxs-lookup"><span data-stu-id="1147c-130">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1147c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1147c-131">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="1147c-132">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="1147c-132">File and stream I/O</span></span>](index.md)
