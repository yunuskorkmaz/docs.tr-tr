---
title: 'Nasıl Yapılır: Dosya Sıkıştırma ve Çıkarma'
ms.date: 03/30/2017
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
ms.openlocfilehash: f3e535e13fe91e1a5cb9c868428f5edbb9eac03f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compress-and-extract-files"></a>Nasıl Yapılır: Dosya Sıkıştırma ve Çıkarma
<xref:System.IO.Compression> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için aşağıdaki türleri içerir. Bu tür, okumak ve sıkıştırılmış bir dosya içeriğini değiştirmek için de kullanabilirsiniz:  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 Aşağıdaki örnekler bazı sıkıştırılmış dosyaları ile çalışırken gerçekleştirebileceğiniz işlevlerin gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl oluşturulup kullanarak bir .zip dosya adı uzantısına sahip sıkıştırılmış bir dosya Ayıkla gösterir <xref:System.IO.Compression.ZipFile> sınıfı. Yeni bir .zip dosyasına bir klasörün içeriğini sıkıştırır ve bu içeriği yeni bir klasöre ayıklar. Kullanılacak <xref:System.IO.Compression.ZipFile> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, var olan bir .zip dosyasını içeriğini yinelemek ve bir .txt uzantısı olan dosyaları ayıklayın gösterilmektedir. Kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve <xref:System.IO.Compression.ZipArchiveEntry> sınıfı sıkıştırılmış dosyası içinde ayrı girişleri inceleyin. Bir genişletme yöntemi kullanır (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) için <xref:System.IO.Compression.ZipArchiveEntry> nesnesi. Genişletme yöntemi kullanılabilir <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> sınıfı. Kullanılacak <xref:System.IO.Compression.ZipFileExtensions> sınıfı, başvurmalıdır `System.IO.Compression.FileSystem` projenizdeki derleme.  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek kullanır <xref:System.IO.Compression.ZipArchive> var olan bir .zip dosyasına erişmek için sınıf ve yeni bir dosya sıkıştırılmış dosyasına ekler. Varolan .zip dosyasına eklediğinizde yeni dosyası sıkıştırılmış.  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aynı zamanda <xref:System.IO.Compression.GZipStream> ve <xref:System.IO.Compression.DeflateStream> sıkıştırmak ve veri genişletmek için sınıflar. Bunlar aynı sıkıştırma algoritması kullanır. Sıkıştırılmış <xref:System.IO.Compression.GZipStream> .gz uzantısına sahip bir dosyaya yazılır nesneleri tarafından sağlanan yöntemleri ek olarak birçok ortak araçlarını kullanarak sıkıştırması açılmış <xref:System.IO.Compression.GZipStream>. Bu örnek sıkıştırmak ve kullanarak bir dosya dizininde genişletmek nasıl gösterir <xref:System.IO.Compression.GZipStream> sınıfı.  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
