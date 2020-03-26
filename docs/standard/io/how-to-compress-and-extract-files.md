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
# <a name="how-to-compress-and-extract-files"></a>Nasıl yapılır: Dosyaları sıkıştırın ve ayıklayın

Ad <xref:System.IO.Compression> alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmak için aşağıdaki türleri içerir. Sıkıştırılmış bir dosyanın içeriğini okumak ve değiştirmek için bu türleri de kullanabilirsiniz.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Aşağıdaki örnekler, sıkıştırılmış dosyalarla gerçekleştirebileceğiniz bazı işlemleri gösterir. Bu örnekler, projenize aşağıdaki NuGet paketlerinin eklenmesini gerektirir:

- [System.IO.Sıkıştırma](https://www.nuget.org/packages/System.IO.Compression)
- [System.IO.Compression.ZipFile](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

.NET Framework kullanıyorsanız, projenize bu iki kitaplık için başvurular ekleyin:

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a>Örnek 1: .zip dosyası oluşturma ve ayıklama

Aşağıdaki örnek, sınıfı kullanarak sıkıştırılmış bir *.zip* dosyasının <xref:System.IO.Compression.ZipFile> nasıl oluşturulup ayıklanılmayı gösterir. Örnek, bir klasörün içeriğini yeni bir *.zip* dosyasına sıkıştırır ve zip'i yeni bir klasöre ayıklar.

Örneği çalıştırmak için, program klasörünüzde bir *başlangıç* klasörü oluşturun ve zip dosyalarıyla doldurun.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Örnek 2: Belirli dosya uzantılarını ayıklayın

Sonraki örnek, varolan bir *.zip* dosyasının içeriğini yineler ve *.txt* uzantılı dosyaları ayıklar. Fermuara <xref:System.IO.Compression.ZipArchive> erişmek için sınıfı <xref:System.IO.Compression.ZipArchiveEntry> ve tek tek girişleri incelemek için sınıfı kullanır. Nesnenin <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> <xref:System.IO.Compression.ZipArchiveEntry> uzantı yöntemi <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfta kullanılabilir.

Örneği çalıştırmak için program klasörünüze *result.zip* adlı bir *.zip* dosyası yerleştirin. İstendiğinde, ayıklamak için bir klasör adı sağlayın.

> [!IMPORTANT]
> Dosyaların gün açmakısmını açarken, içine sızdırdığınız dizinden kaçabilen kötü amaçlı dosya yollarını aramanız gerekir. Bu bir yol geçiş saldırısı olarak bilinir. Aşağıdaki örnek, kötü amaçlı dosya yollarının nasıl denetlenebildiğini gösterir ve fermuarını açmak için güvenli bir yol sağlar.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Örnek 3: Varolan bir zip'e dosya ekleme

Aşağıdaki örnek, <xref:System.IO.Compression.ZipArchive> varolan bir *.zip* dosyasına erişmek için sınıfı kullanır ve dosyaya bir dosya ekler. Varolan zip'e eklediğinizde yeni dosya sıkıştırılır.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Örnek 4: .gz dosyalarını sıkıştırın ve dekomprese edin

Verileri sıkıştırmak <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak için sınıfları da kullanabilirsiniz. Aynı sıkıştırma algoritmasını kullanıyorlar. Bir <xref:System.IO.Compression.GZipStream> *.gz* dosyasına yazılan nesneleri birçok ortak araç kullanarak dekomprese edebilirsiniz. Aşağıdaki örnek, sınıfı kullanarak dosyaların dizinini nasıl sıkıştırıp <xref:System.IO.Compression.GZipStream> dekomsadan arındırılabildiğini gösterir:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
