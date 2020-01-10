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
# <a name="how-to-compress-and-extract-files"></a>Nasıl yapılır: dosyaları sıkıştırma ve ayıklama

<xref:System.IO.Compression> ad alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmayı açma için aşağıdaki türleri içerir. Bu türleri, sıkıştırılmış bir dosyanın içeriğini okumak ve değiştirmek için de kullanabilirsiniz.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Aşağıdaki örneklerde, sıkıştırılmış dosyalarla gerçekleştirebileceğiniz bazı işlemler gösterilmektedir.

## <a name="example-1-create-and-extract-a-zip-file"></a>Örnek 1: bir. zip dosyası oluşturma ve ayıklama

Aşağıdaki örnek, <xref:System.IO.Compression.ZipFile> sınıfını kullanarak sıkıştırılmış bir *. zip* dosyası oluşturmayı ve ayıklamayı gösterir. Örnek, bir klasörün içeriğini yeni bir *. zip* dosyasına sıkıştırır ve sonra zip 'i yeni bir klasöre ayıklar. 

Örneği çalıştırmak için, program klasörünüzde bir *Başlangıç* klasörü oluşturun ve dosyaları ZIP 'e göre doldurun. 

"ZipFile" adı geçerli bağlamda mevcut değil, "derleme hatası" varsa, projenize `System.IO.Compression.FileSystem` derlemesine bir başvuru ekleyin.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Örnek 2: belirli dosya uzantılarını ayıklama

Sonraki örnek, var olan bir *. zip* dosyasının içeriği boyunca yinelenir ve *. txt* uzantısına sahip dosyaları ayıklar. ZIP 'e erişmek için <xref:System.IO.Compression.ZipArchive> sınıfını ve tek tek girdileri incelemek için <xref:System.IO.Compression.ZipArchiveEntry> sınıfını kullanır. <xref:System.IO.Compression.ZipArchiveEntry> nesnesi için <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> genişletme yöntemi <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfında kullanılabilir. 

Örneği çalıştırmak için program klasörünüze *Result. zip* adlı bir *. zip* dosyası yerleştirin. İstendiğinde, ' a Ayıklanacak bir klasör adı belirtin. 

"ZipFile" adı geçerli bağlamda mevcut değil, "derleme hatası" varsa, projenize `System.IO.Compression.FileSystem` derlemesine bir başvuru ekleyin.

"' ZipArchive ' türü, başvurulmayan bir derlemede tanımlanmıştır," `System.IO.Compression` derlemesine bir başvuru ekleyin. 

> [!IMPORTANT]
> Dosyaları kaldırdığınızda, geri yüklediğiniz dizinden çıkmak için kötü amaçlı dosya yolları araması yapmanız gerekir. Bu, yol çapraz geçişi saldırısı olarak bilinir. Aşağıdaki örnek, kötü amaçlı dosya yollarının nasıl denetleyeceğinizi ve sıkıştırmayı açmak için güvenli bir yol sağlar.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Örnek 3: mevcut bir zip dosyasına dosya ekleme

Aşağıdaki örnek, var olan bir *. zip* dosyasına erişmek için <xref:System.IO.Compression.ZipArchive> sınıfını kullanır ve buna bir dosya ekler. Yeni dosya, var olan zip 'e eklediğinizde sıkıştırılır.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Örnek 4:. gz dosyalarını sıkıştır ve aç

Ayrıca, verileri sıkıştırmak ve açmak için <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sınıflarını da kullanabilirsiniz. Aynı sıkıştırma algoritmasını kullanır. Birçok ortak araç kullanarak bir *. gz* dosyasına yazılan nesneleri <xref:System.IO.Compression.GZipStream> açabilirsiniz. Aşağıdaki örnek, <xref:System.IO.Compression.GZipStream> sınıfını kullanarak bir dosya dizinini nasıl sıkıştırmak ve açmak gösterilmektedir:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
