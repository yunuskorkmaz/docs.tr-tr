---
title: 'Nasıl yapılır: Sıkıştır ve dosyaları ayıklayın'
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
ms.openlocfilehash: 669936d15cfe1ea125ed36ffdfcfd093b6aacbe1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687640"
---
# <a name="how-to-compress-and-extract-files"></a>Nasıl yapılır: Sıkıştır ve dosyaları ayıklayın

<xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içeriyor. Bu türler, okumak ve sıkıştırılmış bir dosyanın içeriğini değiştirmek için de kullanabilirsiniz:

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

Aşağıdaki örnekler sıkıştırılmış dosyalarıyla çalışırken gerçekleştirebileceğiniz işlevlerin bazılarını gösterir.

## <a name="example-1---create-and-extract-a-zip-file"></a>Örnek 1 - oluşturma ve bir .zip dosyasını çıkartın

Aşağıdaki örneği kullanarak bir .zip dosya adı uzantısına sahip sıkıştırılmış bir dosya oluşturun ve gösterilmektedir <xref:System.IO.Compression.ZipFile> sınıfı. Yeni bir .zip dosyasına bir klasörün içeriğini sıkıştırır ve sonra bu içeriği yeni bir klasöre ayıklar. Kullanılacak <xref:System.IO.Compression.ZipFile> sınıfı başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>Örnek 2 - Extract belirli dosya uzantıları

Sonraki örnek, bir .txt uzantısına sahip dosyaları ayıklayın ve var olan bir .zip dosyasının içeriğini yineleme gösterilmektedir. Kullandığı <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> sıkıştırılmış dosyasındaki girişler incelemek için sınıf. Bir uzantı yöntemini kullanır (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) için <xref:System.IO.Compression.ZipArchiveEntry> nesne. Genişletme yöntemi kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı. Kullanılacak <xref:System.IO.Compression.ZipFileExtensions> sınıfı başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.

> [!IMPORTANT]
> Dosyaların sıkıştırmasını açarken, kötü amaçlı dosya yolları, bir çıkış dizini içine sıkıştırmasını istediğiniz kaçış yapılacağını da aramanız gerekir. Bu yol çapraz geçişi saldırısını bilinir.

Aşağıdaki örnek, kötü amaçlı dosya yolları için nasıl kontrol edileceğini göstermektedir ve sıkıştırmasını güvenli bir yol sağlar:

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>Örnek 3 - mevcut bir .zip dosyası olarak yeni bir dosya ekleme

Aşağıdaki örnekte <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve sıkıştırılmış dosya için yeni bir dosya ekler. Varolan bir .zip dosyasına eklediğinizde yeni dosyayı sıkıştırılmış.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>Örnek 4 - sıkıştırma ve .gz dosyaları dizini açılamadı

Ayrıca <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve verileri genişletmek için sınıflar. Bunlar aynı sıkıştırma algoritması kullanır. Sıkıştırılmış <xref:System.IO.Compression.GZipStream> .gz uzantısına sahip bir dosyaya yazılır nesneler tarafından sağlanan yöntemleri yanı sıra birçok yaygın araçları kullanarak sıkıştırması açılmış <xref:System.IO.Compression.GZipStream>. Aşağıdaki örnek, sıkıştırma ve kullanarak bir dosya dizininde genişletmek gösterilmektedir <xref:System.IO.Compression.GZipStream> sınıfı:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
