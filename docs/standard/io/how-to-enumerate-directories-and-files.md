---
title: 'Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de83395df9e8c89a92e85b96ddd15e9f0be6ad5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207700"
---
# <a name="how-to-enumerate-directories-and-files"></a>Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma
Dizinleri ve dosyaları numaralandırma bir sıralanabilir koleksiyonun adlarının dizisini döndüren yöntemler kullanarak. Numaralandırılabilir bir koleksiyonunu döndüren yöntemler de kullanabilirsiniz <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesneleri. Dizin ve dosyaların büyük koleksiyonlarla çalışıyorsanız numaralandırılabilir koleksiyonları diziler daha iyi performans sağlar.  
  
 Bu yöntemlerden alınan numaralandırılabilir koleksiyonları sağlamak için de kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> parametresi koleksiyonun oluşturucular için sınıflar gibi <xref:System.Collections.Generic.List%601> sınıfı.  
  
 Yalnızca dizinleri ve dosyaları adlarını almak istiyorsanız, numaralandırma yöntemlerini kullanan <xref:System.IO.Directory> sınıfı. Dizinleri ve dosyaları diğer özelliklerini almak istediğiniz kullanırsanız <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıfları.  
  
 Aşağıdaki tabloda, numaralandırılabilir koleksiyonları döndüren yöntemler için bir kılavuz sağlar.  
  
|Numaralandırılacak|Döndürülecek bir sıralanabilir koleksiyonun|Kullanılacak yöntemi|  
|------------------|-------------------------------------|-------------------|  
|Dizinleri|Dizin adları|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Dizin bilgilerini (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dosyalar|Dosya adları|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Dosya bilgileri (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya sistemi bilgileri|Dosya sistemi girişleri|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Dosya sistemi bilgileri (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Kullanarak bir üst dizin dizinlerindeki tüm dosyaları hemen numaralandırabilirsiniz rağmen <xref:System.IO.SearchOption.AllDirectories> arama seçeneği tarafından sağlanan <xref:System.IO.SearchOption> numaralandırma, yetkisiz erişim özel durumlar (<xref:System.UnauthorizedAccessException>) sabit listesine neden olabilir tamamlanmamış olabilir. Bu özel durumlar olası bunları catch ve ilk dizinleri numaralandırma ve ardından dosyaları numaralandırma devam edin.  
  
### <a name="to-enumerate-directory-names"></a>Dizin adlarını listelemek için  
  
-   Kullanım <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yoldaki gidemez adlarının bir listesini almak için yöntemi.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Dosya adlarında bir dizin ve alt dizinleri numaralandırma  
  
-   Kullanım <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> bir dizin ve (isteğe bağlı) alt dizinlerinde arama yapın ve belirli bir arama deseniyle eşleşen dosya adlarının bir listesini almak için yöntemi.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>DirectoryInfo nesnelerden oluşan bir koleksiyon numaralandırma  
  
-   Kullanım <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> en üst düzey dizinler koleksiyonu almak için yöntemi.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Tüm dizinlerde FileInfo nesnelerden oluşan bir koleksiyon numaralandırma  
  
-   Kullanım <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> tüm dizinlerde belirtilen arama bir desenle eşleşen dosyaları koleksiyonu almak için yöntemi. Bu örnekte, ilk olası yetkisiz erişim özel durumları yakalamak için üst düzey dizinleri numaralandırır ve ardından dosyaları listeler.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
