---
title: "Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d0f22853210144881e49c4192ea38a5c3e57cda
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-directories-and-files"></a>Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma
Dizeleri adlarının numaralandırılabilir bir koleksiyonu döndüren yöntemler kullanarak dizinleri ve dosyaları numaralandırma. Numaralandırılabilir bir koleksiyonu döndüren yöntemler de kullanabilirsiniz <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesneleri. Dizin ve dosyaların büyük koleksiyonlarla çalışırken numaralandırılabilir koleksiyonları diziler daha iyi performans sağlar.  
  
 Sağlamak için bu yöntemlerden elde numaralandırılabilir koleksiyonları kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> parametresi koleksiyonunun oluşturucuları için sınıflar gibi <xref:System.Collections.Generic.List%601> sınıfı.  
  
 Yalnızca dizinleri ve dosyaları adlarını almak istiyorsanız, numaralandırma yöntemlerini kullanın <xref:System.IO.Directory> sınıfı. Dizinleri ve dosyaları diğer özelliklerini edinmek istiyorsanız, kullanmak <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıfları.  
  
 Aşağıdaki tabloda numaralandırılabilir koleksiyonları döndüren yöntemler için bir kılavuz sağlar.  
  
|Numaralandırılacak|Döndürülecek numaralandırılabilir koleksiyonu|Kullanılacak yöntemi|  
|------------------|-------------------------------------|-------------------|  
|Dizinleri|Dizin adları|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Dizin bilgileri (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dosyalar|Dosya adları|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Dosya bilgileri (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya sistemi bilgileri|Dosya sistemi girişleri|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Dosya sistemi bilgileri (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Kullanarak bir üst dizine dizinlerindeki tüm dosyaları hemen numaralandırabilir rağmen <xref:System.IO.SearchOption.AllDirectories> arama seçeneği tarafından sağlanan <xref:System.IO.SearchOption> numaralandırma, yetkisiz erişim özel durumları (<xref:System.UnauthorizedAccessException>) numaralandırma neden olabilir tamamlanmamış olabilir. Bu özel durumlar olası varsa, bunları catch ve ilk dizinleri numaralandırma ve dosyaları numaralandırma devam edebilirsiniz.  
  
### <a name="to-enumerate-directory-names"></a>Dizin adlarını numaralandırılamıyor  
  
-   Kullanım <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yoldaki üst düzey dizin adlarının bir listesini elde etmek için yöntemi.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Dosya adları bir dizin ve alt dizinlerinde numaralandırılamıyor  
  
-   Kullanım <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> yöntemi bir dizin ve (isteğe bağlı) dizinlerinden aramak ve belirtilen arama deseniyle eşleşen dosya adlarının bir listesini almak için.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>DirectoryInfo nesneler koleksiyonunu numaralandırılamıyor  
  
-   Kullanım <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> en üst düzey dizinler koleksiyonu elde etmek için yöntemi.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Tüm dizinlerde FileInfo nesneler koleksiyonunu numaralandırılamıyor  
  
-   Kullanım <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> tüm dizinlerde belirtilen arama deseniyle eşleşen dosya koleksiyonunu elde etmek için yöntemi. Bu örnekte, ilk olası yetkisiz erişim özel durumları yakalamak için üst düzey dizinler numaralandırır ve dosyaları sıralar.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosya ve akış t-O](../../../docs/standard/io/index.md)
