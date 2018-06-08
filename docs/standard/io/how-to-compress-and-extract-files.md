---
title: 'Nasıl yapılır: sıkıştırma ve dosyaları ayıklayın'
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
ms.openlocfilehash: f045f2137d65a66ac025c81e58e66c96bcaca031
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827130"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="fef06-102">Nasıl yapılır: sıkıştırma ve dosyaları ayıklayın</span><span class="sxs-lookup"><span data-stu-id="fef06-102">How to: Compress and extract files</span></span>

<span data-ttu-id="fef06-103"><xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fef06-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="fef06-104">Bu tür, okumak ve sıkıştırılmış bir dosya içeriğini değiştirmek için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fef06-104">You can also use these types to read and modify the contents of a compressed file:</span></span>

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="fef06-105">Aşağıdaki örnekler bazı sıkıştırılmış dosyaları ile çalışırken gerçekleştirebileceğiniz işlevlerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="fef06-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>

## <a name="example-1---create-and-extract-a-zip-file"></a><span data-ttu-id="fef06-106">Örnek 1 - oluşturun ve bir .zip dosyasını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="fef06-106">Example 1 - Create and extract a .zip file</span></span>

<span data-ttu-id="fef06-107">Aşağıdaki örnek oluşturun ve kullanarak bir .zip dosya adı uzantısına sahip sıkıştırılmış bir dosya ayıklayın gösterilmektedir <xref:System.IO.Compression.ZipFile> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fef06-107">The following example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="fef06-108">Yeni bir .zip dosyasına bir klasörün içeriğini sıkıştırır ve bu içeriği yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="fef06-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="fef06-109">Kullanılacak <xref:System.IO.Compression.ZipFile> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.</span><span class="sxs-lookup"><span data-stu-id="fef06-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a><span data-ttu-id="fef06-110">Örnek 2 - Extract belirli dosya uzantıları</span><span class="sxs-lookup"><span data-stu-id="fef06-110">Example 2 - Extract specific file extensions</span></span>

<span data-ttu-id="fef06-111">Aşağıdaki örnek, var olan bir .zip dosyasını içeriğini yinelemek ve bir .txt uzantısı olan dosyaları ayıklayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fef06-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="fef06-112">Kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> sınıfı sıkıştırılmış dosyası içinde ayrı girişleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="fef06-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="fef06-113">Bir genişletme yöntemi kullanır (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) için <xref:System.IO.Compression.ZipArchiveEntry> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fef06-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="fef06-114">Genişletme yöntemi kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fef06-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fef06-115">Kullanılacak <xref:System.IO.Compression.ZipFileExtensions> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.</span><span class="sxs-lookup"><span data-stu-id="fef06-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fef06-116">Dosyaları olan zaman çıkışı dizinin içine sıkıştırmasını istediğiniz kaçınmak kötü amaçlı dosya yolları aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef06-116">When unzipping files, you must look for malicious file paths which can escape out of the directory where you want to unzip into.</span></span> <span data-ttu-id="fef06-117">Bu yol geçişi saldırı olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="fef06-117">This is known as a path traversal attack.</span></span>

<span data-ttu-id="fef06-118">Aşağıdaki örnek, kötü amaçlı dosya yolları için denetleyin yapmayı gösteren ve sıkıştırmasını açmak için güvenli bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="fef06-118">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip:</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a><span data-ttu-id="fef06-119">Örnek 3 - yeni bir dosya varolan bir .zip dosyasına Ekle</span><span class="sxs-lookup"><span data-stu-id="fef06-119">Example 3 - Add a new file to an existing .zip file</span></span>

<span data-ttu-id="fef06-120">Aşağıdaki örnek kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve yeni bir dosya sıkıştırılmış dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="fef06-120">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="fef06-121">Varolan .zip dosyasına eklediğinizde yeni dosyası sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="fef06-121">The new file gets compressed when you add it to the existing .zip file.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a><span data-ttu-id="fef06-122">Örnek 4 - Sıkıştır ve bir dizin .gz dosyaların sıkıştırmasını</span><span class="sxs-lookup"><span data-stu-id="fef06-122">Example 4 - Compress and decompress a directory of .gz files</span></span>

<span data-ttu-id="fef06-123">Aynı zamanda <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve veri genişletmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="fef06-123">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="fef06-124">Bunlar aynı sıkıştırma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="fef06-124">They use the same compression algorithm.</span></span> <span data-ttu-id="fef06-125">Sıkıştırılmış <xref:System.IO.Compression.GZipStream> .gz uzantısına sahip bir dosyaya yazılır nesneleri tarafından sağlanan yöntemleri ek olarak birçok ortak araçlarını kullanarak sıkıştırması açılmış <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="fef06-125">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="fef06-126">Aşağıdaki örnek, sıkıştırmak ve kullanarak bir dosya dizininde genişletmek gösterilmiştir <xref:System.IO.Compression.GZipStream> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="fef06-126">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="fef06-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fef06-127">See also</span></span>

<xref:System.IO.Compression.ZipArchive>  
<xref:System.IO.Compression.ZipFile>  
<xref:System.IO.Compression.ZipArchiveEntry>  
<xref:System.IO.Compression.DeflateStream>  
<xref:System.IO.Compression.GZipStream>  
[<span data-ttu-id="fef06-128">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="fef06-128">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
