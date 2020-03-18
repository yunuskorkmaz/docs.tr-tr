---
title: 'Nasıl yapılır: Dizinleri ve dosyaları sayısal'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707751"
---
# <a name="how-to-enumerate-directories-and-files"></a>Nasıl yapılır: Dizinleri ve dosyaları sayısal
Sayısal koleksiyonlar, büyük dizin ve dosya koleksiyonlarıyla çalışırken dizilerden daha iyi performans sağlar. Dizinleri ve dosyaları doğrulamak için, dizin veya dosya adlarının veya bunların <xref:System.IO.DirectoryInfo> <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesnelerin sayısal bir koleksiyonunu döndüren yöntemler kullanın.  
  
Yalnızca dizin veya dosya adlarını aramak ve döndürmek istiyorsanız, sınıfın numaralandırma <xref:System.IO.Directory> yöntemlerini kullanın. Dizinlerin veya dosyaların diğer özelliklerini aramak ve döndürmek <xref:System.IO.DirectoryInfo> <xref:System.IO.FileSystemInfo> istiyorsanız, sınıfları ve bunları kullanın.  
  
Bu yöntemlerden elde edilen sayısal koleksiyonları, <xref:System.Collections.Generic.IEnumerable%601> tahsilat <xref:System.Collections.Generic.List%601>sınıflarının oluşturucuları için parametre olarak kullanabilirsiniz.  
  
Aşağıdaki tabloda, dosya ve dizinlerin sayısal koleksiyonlarını döndüren yöntemler özetlenmiştir:  
  
|Arama ve dönüş için|Kullanım yöntemi|  
|------------------|-------------------------------------|-------------------|  
|Dizin adları|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dizin bilgileri<xref:System.IO.DirectoryInfo>( )|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dosya adları|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya bilgileri<xref:System.IO.FileInfo>( )|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş adları|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş<xref:System.IO.FileSystemInfo>bilgileri ( )|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Dizin ve dosya adları |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> İsteğe bağlı <xref:System.IO.SearchOption.AllDirectories> <xref:System.IO.SearchOption> numaralandırma seçeneğini kullanarak bir üst dizinin alt dizilişlerinde bulunan tüm dosyaları hemen <xref:System.UnauthorizedAccessException> numaralandırmanıza rağmen, hatalar numaralandırmayı eksik yapabilir. Bu özel durumları önce dizinleri ve sonra dosyaları sayısallayarak yakalayabilirsiniz.  
  
## <a name="examples-use-the-directory-class"></a>Örnekler: Dizin sınıfını kullanın  
  
Aşağıdaki örnek, <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen bir yoltaki üst düzey dizin adlarının listesini almak için yöntemi kullanır.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Aşağıdaki örnek, <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> belirli bir desenle eşleşen bir dizindeki tüm dosya adlarını ve alt dizinleri özyinelemeli olarak listelemek için yöntemi kullanır. Daha sonra her dosyanın her satırını okur ve dosya adları ve yolları ile belirtilen bir dize içeren satırları görüntüler.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Örnekler: DirectoryInfo sınıfını kullanın  
  
Aşağıdaki örnek, <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> belirli <xref:System.DateTime> bir değerden daha önce olan <xref:System.IO.FileSystemInfo.CreationTimeUtc> üst düzey dizinkoleksiyonunu listelemek için yöntemi kullanır.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Aşağıdaki örnek, <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> 10MB'yi <xref:System.IO.FileInfo.Length> aşan tüm dosyaları listelemek için yöntemi kullanır. Bu örnek, olası yetkisiz erişim özel durumlarını yakalamak için önce üst düzey dizinleri günceller ve sonra dosyaları günceller.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
