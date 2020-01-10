---
title: 'Nasıl yapılır: dizinleri ve dosyaları numaralandırma'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707751"
---
# <a name="how-to-enumerate-directories-and-files"></a>Nasıl yapılır: dizinleri ve dosyaları numaralandırma
Sıralanabilir koleksiyonlar, büyük dizin ve dosya koleksiyonlarıyla çalışırken dizilerden daha iyi performans sağlar. Dizinleri ve dosyaları numaralandırmak için dizin veya dosya adlarının veya <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>veya <xref:System.IO.FileSystemInfo> nesnelerinin sıralanabilir bir koleksiyonunu döndüren yöntemleri kullanın.  
  
Yalnızca dizinlerin veya dosyaların adlarını aramak ve döndürmek istiyorsanız, <xref:System.IO.Directory> sınıfının numaralandırma yöntemlerini kullanın. Dizinlerin veya dosyaların diğer özelliklerini aramak ve döndürmek istiyorsanız <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıflarını kullanın.  
  
Bu yöntemlerdeki sıralanabilir koleksiyonları, <xref:System.Collections.Generic.List%601>gibi koleksiyon sınıflarının oluşturucuları için <xref:System.Collections.Generic.IEnumerable%601> parametresi olarak kullanabilirsiniz.  
  
Aşağıdaki tabloda, dosya ve dizinlerin numaralandırılabilir koleksiyonlarını döndüren yöntemler özetlenmektedir:  
  
|Aramak ve döndürmek için|Use yöntemi|  
|------------------|-------------------------------------|-------------------|  
|Dizin adları|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dizin bilgileri (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dosya adları|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya bilgileri (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş adları|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş bilgileri (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Dizin ve dosya adları |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> İsteğe bağlı <xref:System.IO.SearchOption> sabit listesinin <xref:System.IO.SearchOption.AllDirectories> seçeneğini kullanarak bir üst dizinin alt dizinlerindeki tüm dosyaları hemen numaralandırabilirsiniz, ancak <xref:System.UnauthorizedAccessException> hatalar numaralandırmayı tamamlanmamış hale getirir. Önce dizinleri listeleyerek ve sonra dosyaları numaralandırarak bu özel durumları yakalayabilir.  
  
## <a name="examples-use-the-directory-class"></a>Örnekler: Dizin sınıfını kullanma  
  
Aşağıdaki örnek, belirtilen yoldaki en üst düzey dizin adlarının listesini almak için <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> yöntemini kullanır.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Aşağıdaki örnek, belirli bir kalıpla eşleşen bir dizin ve alt dizinler içindeki tüm dosya adlarını yinelemeli olarak numaralandırmak için <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> yöntemini kullanır. Sonra her bir dosyanın her bir satırını okur ve belirtilen bir dizeyi içeren satırları dosya adlarıyla ve yollarıyla görüntüler.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Örnekler: DirectoryInfo sınıfını kullanma  
  
Aşağıdaki örnek, <xref:System.IO.FileSystemInfo.CreationTimeUtc> belirli bir <xref:System.DateTime> değerinden daha eski olan en üst düzey dizinlerin bir koleksiyonunu listelemek için <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> yöntemini kullanır.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Aşağıdaki örnek, <xref:System.IO.FileInfo.Length> 10 MB 'ı aşan tüm dosyaları listelemek için <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> yöntemini kullanır. Bu örnek öncelikle, olası yetkisiz erişim özel durumlarını yakalamak ve sonra dosyaları numaralandırmaları için üst düzey dizinleri numaralandırır.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
