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
ms.openlocfilehash: bcb10426175c1f2cabeec6d8d4f8d2ed74e5e3b4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291883"
---
# <a name="how-to-enumerate-directories-and-files"></a>Nasıl yapılır: dizinleri ve dosyaları numaralandırma
Sıralanabilir koleksiyonlar, büyük dizin ve dosya koleksiyonlarıyla çalışırken dizilerden daha iyi performans sağlar. Dizinleri ve dosyaları numaralandırmak için dizin veya dosya adlarının veya bunların veya nesnelerinin sıralanabilir bir koleksiyonunu döndüren yöntemleri kullanın <xref:System.IO.DirectoryInfo> <xref:System.IO.FileInfo> <xref:System.IO.FileSystemInfo> .  
  
Yalnızca dizinlerin veya dosyaların adlarını aramak ve döndürmek istiyorsanız, sınıfının numaralandırma yöntemlerini kullanın <xref:System.IO.Directory> . Dizinlerin veya dosyaların diğer özelliklerini aramak ve döndürmek istiyorsanız, <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıflarını kullanın.  
  
Bu yöntemlerdeki sıralanabilir koleksiyonları, <xref:System.Collections.Generic.IEnumerable%601> gibi koleksiyon sınıflarının oluşturucuları için parametre olarak kullanabilirsiniz <xref:System.Collections.Generic.List%601> .  
  
Aşağıdaki tabloda, dosya ve dizinlerin numaralandırılabilir koleksiyonlarını döndüren yöntemler özetlenmektedir:  
  
|Aramak ve döndürmek için|Use yöntemi|  
|------------------|-------------------------------------|-------------------|  
|Dizin adları|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dizin bilgileri ( <xref:System.IO.DirectoryInfo> )|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dosya adları|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya bilgileri ( <xref:System.IO.FileInfo> )|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş adları|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş bilgileri ( <xref:System.IO.FileSystemInfo> )|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Dizin ve dosya adları |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> İsteğe bağlı sabit listesi seçeneğini kullanarak bir üst dizinin alt dizinlerindeki tüm dosyaları hemen numaralandırabilseniz de <xref:System.IO.SearchOption.AllDirectories> <xref:System.IO.SearchOption> <xref:System.UnauthorizedAccessException> hatalar, numaralandırmayı tamamlanmamış hale getirir. Önce dizinleri listeleyerek ve sonra dosyaları numaralandırarak bu özel durumları yakalayabilir.  
  
## <a name="examples-use-the-directory-class"></a>Örnekler: Dizin sınıfını kullanma  
  
Aşağıdaki örnek, <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yoldaki en üst düzey dizin adlarının listesini almak için yöntemini kullanır.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Aşağıdaki örnek, <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> belirli bir kalıpla eşleşen bir dizin ve alt dizinler içindeki tüm dosya adlarını yinelemeli olarak numaralandırmak için yöntemini kullanır. Sonra her bir dosyanın her bir satırını okur ve belirtilen bir dizeyi içeren satırları dosya adlarıyla ve yollarıyla görüntüler.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Örnekler: DirectoryInfo sınıfını kullanma  
  
Aşağıdaki örnek, <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> <xref:System.IO.FileSystemInfo.CreationTimeUtc> belirli bir değerden daha eski olan en üst düzey dizinlerin bir koleksiyonunu listelemek için yöntemini kullanır <xref:System.DateTime> .  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Aşağıdaki örnek, <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> 10 MB 'ı aşan tüm dosyaları listelemek için yöntemini kullanır <xref:System.IO.FileInfo.Length> . Bu örnek öncelikle, olası yetkisiz erişim özel durumlarını yakalamak ve sonra dosyaları numaralandırmaları için üst düzey dizinleri numaralandırır.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve akış G/Ç](index.md)
