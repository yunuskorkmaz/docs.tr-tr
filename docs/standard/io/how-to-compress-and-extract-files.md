---
title: 'Nasıl yapılır: Dosyaları sıkıştırın ve ayıklayın'
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
ms.openlocfilehash: 10f990401830bc5f77176f4e586f15f7dd75ff14
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248023"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="b4769-102">Nasıl yapılır: Dosyaları sıkıştırın ve ayıklayın</span><span class="sxs-lookup"><span data-stu-id="b4769-102">How to: Compress and extract files</span></span>

<span data-ttu-id="b4769-103">Ad <xref:System.IO.Compression> alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmak için aşağıdaki türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4769-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="b4769-104">Sıkıştırılmış bir dosyanın içeriğini okumak ve değiştirmek için bu türleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4769-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="b4769-105">Aşağıdaki örnekler, sıkıştırılmış dosyalarla gerçekleştirebileceğiniz bazı işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4769-105">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="b4769-106">Bu örnekler, projenize aşağıdaki NuGet paketlerinin eklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b4769-106">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="b4769-107">System.IO.Sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="b4769-107">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="b4769-108">System.IO.Compression.ZipFile</span><span class="sxs-lookup"><span data-stu-id="b4769-108">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="b4769-109">.NET Framework kullanıyorsanız, projenize bu iki kitaplık için başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b4769-109">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="b4769-110">Örnek 1: .zip dosyası oluşturma ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="b4769-110">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="b4769-111">Aşağıdaki örnek, sınıfı kullanarak sıkıştırılmış bir *.zip* dosyasının <xref:System.IO.Compression.ZipFile> nasıl oluşturulup ayıklanılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4769-111">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="b4769-112">Örnek, bir klasörün içeriğini yeni bir *.zip* dosyasına sıkıştırır ve zip'i yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="b4769-112">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="b4769-113">Örneği çalıştırmak için, program klasörünüzde bir *başlangıç* klasörü oluşturun ve zip dosyalarıyla doldurun.</span><span class="sxs-lookup"><span data-stu-id="b4769-113">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="b4769-114">Örnek 2: Belirli dosya uzantılarını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="b4769-114">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="b4769-115">Sonraki örnek, varolan bir *.zip* dosyasının içeriğini yineler ve *.txt* uzantılı dosyaları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="b4769-115">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="b4769-116">Fermuara <xref:System.IO.Compression.ZipArchive> erişmek için sınıfı <xref:System.IO.Compression.ZipArchiveEntry> ve tek tek girişleri incelemek için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4769-116">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="b4769-117">Nesnenin <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> <xref:System.IO.Compression.ZipArchiveEntry> uzantı yöntemi <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfta kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4769-117">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="b4769-118">Örneği çalıştırmak için program klasörünüze *result.zip* adlı bir *.zip* dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b4769-118">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="b4769-119">İstendiğinde, ayıklamak için bir klasör adı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b4769-119">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4769-120">Dosyaların gün açmakısmını açarken, içine sızdırdığınız dizinden kaçabilen kötü amaçlı dosya yollarını aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4769-120">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="b4769-121">Bu bir yol geçiş saldırısı olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="b4769-121">This is known as a path traversal attack.</span></span> <span data-ttu-id="b4769-122">Aşağıdaki örnek, kötü amaçlı dosya yollarının nasıl denetlenebildiğini gösterir ve fermuarını açmak için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4769-122">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="b4769-123">Örnek 3: Varolan bir zip'e dosya ekleme</span><span class="sxs-lookup"><span data-stu-id="b4769-123">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="b4769-124">Aşağıdaki örnek, <xref:System.IO.Compression.ZipArchive> varolan bir *.zip* dosyasına erişmek için sınıfı kullanır ve dosyaya bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="b4769-124">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="b4769-125">Varolan zip'e eklediğinizde yeni dosya sıkıştırılır.</span><span class="sxs-lookup"><span data-stu-id="b4769-125">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="b4769-126">Örnek 4: .gz dosyalarını sıkıştırın ve dekomprese edin</span><span class="sxs-lookup"><span data-stu-id="b4769-126">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="b4769-127">Verileri sıkıştırmak <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak için sınıfları da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4769-127">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="b4769-128">Aynı sıkıştırma algoritmasını kullanıyorlar.</span><span class="sxs-lookup"><span data-stu-id="b4769-128">They use the same compression algorithm.</span></span> <span data-ttu-id="b4769-129">Bir <xref:System.IO.Compression.GZipStream> *.gz* dosyasına yazılan nesneleri birçok ortak araç kullanarak dekomprese edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4769-129">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="b4769-130">Aşağıdaki örnek, sınıfı kullanarak dosyaların dizinini nasıl sıkıştırıp <xref:System.IO.Compression.GZipStream> dekomsadan arındırılabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="b4769-130">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b4769-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4769-131">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="b4769-132">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="b4769-132">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
