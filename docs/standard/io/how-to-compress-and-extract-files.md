---
title: 'Nasıl yapılır: dosyaları sıkıştırma ve ayıklama'
description: System. ıO. Compression kullanarak dosyaları ayıkla & ayıklayın. ZipFile, ZipArchive, ZipArchiveEntry, DeflateStream & GZipStream kullanan örneklere bakın.
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
ms.openlocfilehash: c13f464432aa6f67136d3a844bdeda256e7ab9b6
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769242"
---
# <a name="how-to-compress-and-extract-files"></a>Nasıl yapılır: dosyaları sıkıştırma ve ayıklama

<xref:System.IO.Compression>Ad alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmayı açma için aşağıdaki türleri içerir. Bu türleri, sıkıştırılmış bir dosyanın içeriğini okumak ve değiştirmek için de kullanabilirsiniz.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Aşağıdaki örneklerde, sıkıştırılmış dosyalarla gerçekleştirebileceğiniz bazı işlemler gösterilmektedir. Bu örnekler, projenize aşağıdaki NuGet paketlerinin eklenmesini gerektirir:

- [System. ıO. Compression](https://www.nuget.org/packages/System.IO.Compression)
- [System.IO.Compression.Zipdosyası](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

.NET Framework kullanıyorsanız, projenize bu iki kitaplıklara başvurular ekleyin:

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a>Örnek 1: bir. zip dosyası oluşturma ve ayıklama

Aşağıdaki örnek, sınıfını kullanarak sıkıştırılmış bir *. zip* dosyası oluşturmayı ve ayıklamayı gösterir <xref:System.IO.Compression.ZipFile> . Örnek, bir klasörün içeriğini yeni bir *. zip* dosyasına sıkıştırır ve sonra zip 'i yeni bir klasöre ayıklar.

Örneği çalıştırmak için, program klasörünüzde bir *Başlangıç* klasörü oluşturun ve dosyaları ZIP 'e göre doldurun.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Örnek 2: belirli dosya uzantılarını ayıklama

Sonraki örnek, var olan bir *. zip* dosyasının içeriği boyunca yinelenir ve *. txt* uzantısına sahip dosyaları ayıklar. <xref:System.IO.Compression.ZipArchive>ZIP 'e erişmek için sınıfını ve <xref:System.IO.Compression.ZipArchiveEntry> tek tek girişleri incelemek için sınıfını kullanır. Nesnesinin genişletme yöntemi <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> <xref:System.IO.Compression.ZipArchiveEntry> <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfında kullanılabilir.

Örneği çalıştırmak için program klasörünüze *result.zip* adlı bir *. zip* dosyası yerleştirin. İstendiğinde, ' a Ayıklanacak bir klasör adı belirtin.

> [!IMPORTANT]
> Dosyaları kaldırdığınızda, geri yüklediğiniz dizinden çıkmak için kötü amaçlı dosya yolları araması yapmanız gerekir. Bu, yol çapraz geçişi saldırısı olarak bilinir. Aşağıdaki örnek, kötü amaçlı dosya yollarının nasıl denetleyeceğinizi ve sıkıştırmayı açmak için güvenli bir yol sağlar.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Örnek 3: mevcut bir zip dosyasına dosya ekleme

Aşağıdaki örnek, <xref:System.IO.Compression.ZipArchive> sınıfını var olan bir *. zip* dosyasına erişmek için kullanır ve buna bir dosya ekler. Yeni dosya, var olan zip 'e eklediğinizde sıkıştırılır.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Örnek 4:. gz dosyalarını sıkıştır ve aç

Ayrıca, <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> verileri sıkıştırmak ve açmak için ve sınıflarını da kullanabilirsiniz. Aynı sıkıştırma algoritmasını kullanır. <xref:System.IO.Compression.GZipStream>Birçok ortak araç kullanarak bir *. gz* dosyasına yazılmış nesneleri açabilirsiniz. Aşağıdaki örnek, sınıfını kullanarak bir dosya dizinini nasıl sıkıştırmak ve açmak gösterilmektedir <xref:System.IO.Compression.GZipStream> :

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Dosya ve akış G/Ç](index.md)
