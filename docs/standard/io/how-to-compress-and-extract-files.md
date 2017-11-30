---
title: "Nasıl Yapılır: Dosya Sıkıştırma ve Çıkarma"
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
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="62ece-102">Nasıl Yapılır: Dosya Sıkıştırma ve Çıkarma</span><span class="sxs-lookup"><span data-stu-id="62ece-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="62ece-103"><xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="62ece-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="62ece-104">Bu tür, okumak ve sıkıştırılmış bir dosya içeriğini değiştirmek için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="62ece-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="62ece-105">Aşağıdaki örnekler bazı sıkıştırılmış dosyaları ile çalışırken gerçekleştirebileceğiniz işlevlerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="62ece-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62ece-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="62ece-106">Example</span></span>  
 <span data-ttu-id="62ece-107">Bu örnek nasıl oluşturulup kullanarak bir .zip dosya adı uzantısına sahip sıkıştırılmış bir dosya Ayıkla gösterir <xref:System.IO.Compression.ZipFile> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62ece-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="62ece-108">Yeni bir .zip dosyasına bir klasörün içeriğini sıkıştırır ve bu içeriği yeni bir klasöre ayıklar.</span><span class="sxs-lookup"><span data-stu-id="62ece-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="62ece-109">Kullanılacak <xref:System.IO.Compression.ZipFile> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.</span><span class="sxs-lookup"><span data-stu-id="62ece-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="62ece-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="62ece-110">Example</span></span>  
 <span data-ttu-id="62ece-111">Aşağıdaki örnek, var olan bir .zip dosyasını içeriğini yinelemek ve bir .txt uzantısı olan dosyaları ayıklayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62ece-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="62ece-112">Kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> sınıfı sıkıştırılmış dosyası içinde ayrı girişleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="62ece-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="62ece-113">Bir genişletme yöntemi kullanır (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) için <xref:System.IO.Compression.ZipArchiveEntry> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="62ece-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="62ece-114">Genişletme yöntemi kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62ece-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="62ece-115">Kullanılacak <xref:System.IO.Compression.ZipFileExtensions> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.</span><span class="sxs-lookup"><span data-stu-id="62ece-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="62ece-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="62ece-116">Example</span></span>  
 <span data-ttu-id="62ece-117">Sonraki örnek kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve yeni bir dosya sıkıştırılmış dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="62ece-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="62ece-118">Varolan .zip dosyasına eklediğinizde yeni dosyası sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="62ece-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="62ece-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="62ece-119">Example</span></span>  
 <span data-ttu-id="62ece-120">Aynı zamanda <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve veri genişletmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="62ece-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="62ece-121">Bunlar aynı sıkıştırma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="62ece-121">They use the same compression algorithm.</span></span> <span data-ttu-id="62ece-122">Sıkıştırılmış <xref:System.IO.Compression.GZipStream> .gz uzantısına sahip bir dosyaya yazılır nesneleri tarafından sağlanan yöntemleri ek olarak birçok ortak araçlarını kullanarak sıkıştırması açılmış <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="62ece-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="62ece-123">Bu örnek sıkıştırmak ve kullanarak bir dosya dizininde genişletmek nasıl gösterir <xref:System.IO.Compression.GZipStream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62ece-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="62ece-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62ece-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="62ece-125">Dosya ve akış t-O</span><span class="sxs-lookup"><span data-stu-id="62ece-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
