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
# <a name="how-to-compress-and-extract-files"></a>Nasıl yapılır: sıkıştırma ve dosyaları ayıklayın

<xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içerir. Bu tür, okumak ve sıkıştırılmış bir dosya içeriğini değiştirmek için de kullanabilirsiniz:

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

Aşağıdaki örnekler bazı sıkıştırılmış dosyaları ile çalışırken gerçekleştirebileceğiniz işlevlerin gösterir.

## <a name="example-1---create-and-extract-a-zip-file"></a>Örnek 1 - oluşturun ve bir .zip dosyasını ayıklayın

Aşağıdaki örnek oluşturun ve kullanarak bir .zip dosya adı uzantısına sahip sıkıştırılmış bir dosya ayıklayın gösterilmektedir <xref:System.IO.Compression.ZipFile> sınıfı. Yeni bir .zip dosyasına bir klasörün içeriğini sıkıştırır ve bu içeriği yeni bir klasöre ayıklar. Kullanılacak <xref:System.IO.Compression.ZipFile> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>Örnek 2 - Extract belirli dosya uzantıları

Aşağıdaki örnek, var olan bir .zip dosyasını içeriğini yinelemek ve bir .txt uzantısı olan dosyaları ayıklayın gösterilmektedir. Kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> sınıfı sıkıştırılmış dosyası içinde ayrı girişleri inceleyin. Bir genişletme yöntemi kullanır (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) için <xref:System.IO.Compression.ZipArchiveEntry> nesnesi. Genişletme yöntemi kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı. Kullanılacak <xref:System.IO.Compression.ZipFileExtensions> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.

> [!IMPORTANT]
> Dosyaları olan zaman çıkışı dizinin içine sıkıştırmasını istediğiniz kaçınmak kötü amaçlı dosya yolları aramanız gerekir. Bu yol geçişi saldırı olarak bilinir.

Aşağıdaki örnek, kötü amaçlı dosya yolları için denetleyin yapmayı gösteren ve sıkıştırmasını açmak için güvenli bir yol sağlar:

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>Örnek 3 - yeni bir dosya varolan bir .zip dosyasına Ekle

Aşağıdaki örnek kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve yeni bir dosya sıkıştırılmış dosyasına ekler. Varolan .zip dosyasına eklediğinizde yeni dosyası sıkıştırılmış.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>Örnek 4 - Sıkıştır ve bir dizin .gz dosyaların sıkıştırmasını

Aynı zamanda <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve veri genişletmek için sınıflar. Bunlar aynı sıkıştırma algoritması kullanır. Sıkıştırılmış <xref:System.IO.Compression.GZipStream> .gz uzantısına sahip bir dosyaya yazılır nesneleri tarafından sağlanan yöntemleri ek olarak birçok ortak araçlarını kullanarak sıkıştırması açılmış <xref:System.IO.Compression.GZipStream>. Aşağıdaki örnek, sıkıştırmak ve kullanarak bir dosya dizininde genişletmek gösterilmiştir <xref:System.IO.Compression.GZipStream> sınıfı:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.IO.Compression.ZipArchive>  
<xref:System.IO.Compression.ZipFile>  
<xref:System.IO.Compression.ZipArchiveEntry>  
<xref:System.IO.Compression.DeflateStream>  
<xref:System.IO.Compression.GZipStream>  
[Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
