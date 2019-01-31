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
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255009"
---
# <a name="how-to-compress-and-extract-files"></a>Nasıl yapılır: Sıkıştırma ve çıkarma dosyaları

<xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içeriyor. Bu türler, okumak ve sıkıştırılmış bir dosyanın içeriğini değiştirmek için de kullanabilirsiniz.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Aşağıdaki örnekler, sıkıştırılmış dosyalar ile gerçekleştirebileceğiniz işlemlerin gösterir.

## <a name="example-1-create-and-extract-a-zip-file"></a>Örnek 1: Oluşturma ve bir .zip dosyasını çıkartın

Aşağıdaki örnek nasıl oluşturulacağı ve bir sıkıştırılmış ayıklamak gösterir *.zip* kullanarak dosya <xref:System.IO.Compression.ZipFile> sınıfı. Örnek bir klasörün içeriğini yeni bir sıkıştırır *.zip* dosyasını açın ve ardından zip yeni bir klasöre ayıklar. 

Örneği çalıştırmak için oluşturma bir *Başlat* , program klasöründe ve ZIP dosyalarıyla doldurabilirsiniz. 

"Name 'ZipFile', geçerli bağlamda yok" derleme hatası alırsanız, bir başvuru ekleyin `System.IO.Compression.FileSystem` projenize derleme.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Örnek 2: Belirli dosya uzantılarını ayıklayın

Sonraki örnekte var olan bir içindekiler yinelenir *.zip* dosyayı ve sahip dosyaları bir *.txt* uzantısı. Kullandığı <xref:System.IO.Compression.ZipArchive> zip erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> girişler incelemek için sınıf. Genişletme yöntemi <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> için <xref:System.IO.Compression.ZipArchiveEntry> nesne kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı. 

Örneği çalıştırmak için yerleştirileceği bir *.zip* adlı dosya *result.zip* program klasörünüzde. İstendiğinde, ayıklamak için bir klasör adı sağlayın. 

"Name 'ZipFile', geçerli bağlamda yok" derleme hatası alırsanız, bir başvuru ekleyin `System.IO.Compression.FileSystem` projenize derleme.

"'ZipArchive' başvurulmayan bir derlemede tanımlanan tür" hata alırsanız, bir başvuru ekleyin `System.IO.Compression` projenize derleme. 

> [!IMPORTANT]
> Dosyaların sıkıştırmasını açarken, çıkış dizini içine sıkıştırmasını dışında kötü amaçlı dosya yolları, aramanız gerekir. Bu yol çapraz geçişi saldırısını bilinir. Aşağıdaki örnek, kötü amaçlı dosya yolları için nasıl kontrol edileceğini göstermektedir ve sıkıştırmasını güvenli bir yol sağlar.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Örnek 3: Bir dosya eklemek için var olan bir zip

Aşağıdaki örnekte <xref:System.IO.Compression.ZipArchive> varolan erişmek için sınıf *.zip* dosyası ve bir dosya ekler. Mevcut zip eklediğinizde yeni dosyayı sıkıştırılmış.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Örnek 4: Sıkıştırma ve .gz dosyaları açılamadı

Ayrıca <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve verileri genişletmek için sınıflar. Bunlar aynı sıkıştırma algoritması kullanır. Sıkıştırmasını açıp <xref:System.IO.Compression.GZipStream> yazılan nesnelerin bir *.gz* birçok yaygın araçları kullanarak dosya. Aşağıdaki örnek, sıkıştırma ve kullanarak bir dosya dizininde genişletmek gösterilmektedir <xref:System.IO.Compression.GZipStream> sınıfı:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
