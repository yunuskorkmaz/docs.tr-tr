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
ms.openlocfilehash: 6345b467e9ade085a38de6dc9758b1bd99d1ae62
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708108"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="1c941-102">Nasıl yapılır: dosyaları sıkıştırma ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="1c941-102">How to: Compress and extract files</span></span>

<span data-ttu-id="1c941-103"><xref:System.IO.Compression> ad alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmayı açma için aşağıdaki türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1c941-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="1c941-104">Bu türleri, sıkıştırılmış bir dosyanın içeriğini okumak ve değiştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c941-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="1c941-105">Aşağıdaki örneklerde, sıkıştırılmış dosyalarla gerçekleştirebileceğiniz bazı işlemler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c941-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="1c941-106">Örnek 1: bir. zip dosyası oluşturma ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="1c941-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="1c941-107">Aşağıdaki örnek, <xref:System.IO.Compression.ZipFile> sınıfını kullanarak sıkıştırılmış bir *. zip* dosyası oluşturmayı ve ayıklamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c941-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="1c941-108">Örnek, bir klasörün içeriğini yeni bir *. zip* dosyasına sıkıştırır ve sonra zip 'i yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1c941-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span> 

<span data-ttu-id="1c941-109">Örneği çalıştırmak için, program klasörünüzde bir *Başlangıç* klasörü oluşturun ve dosyaları ZIP 'e göre doldurun.</span><span class="sxs-lookup"><span data-stu-id="1c941-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span> 

<span data-ttu-id="1c941-110">"ZipFile" adı geçerli bağlamda mevcut değil, "derleme hatası" varsa, projenize `System.IO.Compression.FileSystem` derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c941-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="1c941-111">Örnek 2: belirli dosya uzantılarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="1c941-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="1c941-112">Sonraki örnek, var olan bir *. zip* dosyasının içeriği boyunca yinelenir ve *. txt* uzantısına sahip dosyaları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1c941-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="1c941-113">ZIP 'e erişmek için <xref:System.IO.Compression.ZipArchive> sınıfını ve tek tek girdileri incelemek için <xref:System.IO.Compression.ZipArchiveEntry> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c941-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="1c941-114"><xref:System.IO.Compression.ZipArchiveEntry> nesnesi için <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> genişletme yöntemi <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c941-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> 

<span data-ttu-id="1c941-115">Örneği çalıştırmak için program klasörünüze *Result. zip* adlı bir *. zip* dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1c941-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="1c941-116">İstendiğinde, ' a Ayıklanacak bir klasör adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1c941-116">When prompted, provide a folder name to extract to.</span></span> 

<span data-ttu-id="1c941-117">"ZipFile" adı geçerli bağlamda mevcut değil, "derleme hatası" varsa, projenize `System.IO.Compression.FileSystem` derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c941-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="1c941-118">"' ZipArchive ' türü, başvurulmayan bir derlemede tanımlanmıştır," `System.IO.Compression` derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c941-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1c941-119">Dosyaları kaldırdığınızda, geri yüklediğiniz dizinden çıkmak için kötü amaçlı dosya yolları araması yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c941-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="1c941-120">Bu, yol çapraz geçişi saldırısı olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="1c941-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="1c941-121">Aşağıdaki örnek, kötü amaçlı dosya yollarının nasıl denetleyeceğinizi ve sıkıştırmayı açmak için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c941-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="1c941-122">Örnek 3: mevcut bir zip dosyasına dosya ekleme</span><span class="sxs-lookup"><span data-stu-id="1c941-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="1c941-123">Aşağıdaki örnek, var olan bir *. zip* dosyasına erişmek için <xref:System.IO.Compression.ZipArchive> sınıfını kullanır ve buna bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="1c941-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="1c941-124">Yeni dosya, var olan zip 'e eklediğinizde sıkıştırılır.</span><span class="sxs-lookup"><span data-stu-id="1c941-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="1c941-125">Örnek 4:. gz dosyalarını sıkıştır ve aç</span><span class="sxs-lookup"><span data-stu-id="1c941-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="1c941-126">Ayrıca, verileri sıkıştırmak ve açmak için <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sınıflarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c941-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="1c941-127">Aynı sıkıştırma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c941-127">They use the same compression algorithm.</span></span> <span data-ttu-id="1c941-128">Birçok ortak araç kullanarak bir *. gz* dosyasına yazılan nesneleri <xref:System.IO.Compression.GZipStream> açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c941-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="1c941-129">Aşağıdaki örnek, <xref:System.IO.Compression.GZipStream> sınıfını kullanarak bir dosya dizinini nasıl sıkıştırmak ve açmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1c941-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1c941-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c941-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="1c941-131">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="1c941-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
