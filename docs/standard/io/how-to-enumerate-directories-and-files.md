---
title: 'Nasıl yapılır: Dizinleri ve dosyaları numaralandırma'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 863335cf080dbccd76b38c7222b74637b99ae2f0
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758670"
---
# <a name="how-to-enumerate-directories-and-files"></a>Nasıl yapılır: Dizinleri ve dosyaları numaralandırma
Dizin ve dosyaların büyük koleksiyonlarla çalışıyorsanız numaralandırılabilir koleksiyonları diziler daha iyi performans sağlar. Dizinleri ve dosyaları numaralandırma için numaralandırılabilir bir dizin veya dosya adları topluluğu döndüren yöntemler kullanın veya kendi <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, veya <xref:System.IO.FileSystemInfo> nesneleri.  
  
Arama yapın ve yalnızca dizinleri ve dosyaları adlarını dönmek istiyorsanız, numaralandırma yöntemlerini kullanan <xref:System.IO.Directory> sınıfı. İsterseniz arama ve diğer özelliklerini dizinleri ve dosyaları iade kullanmak <xref:System.IO.DirectoryInfo> ve <xref:System.IO.FileSystemInfo> sınıfları.  
  
Bu yöntemler numaralandırılabilir koleksiyonları kullanabileceğiniz <xref:System.Collections.Generic.IEnumerable%601> parametre koleksiyonu sınıfların oluşturucuları için ister <xref:System.Collections.Generic.List%601>.  
  
Dosyalar ve dizinler numaralandırılabilir koleksiyonları döndüren yöntemler aşağıdaki tabloda özetlenmiştir:  
  
|Arama ve döndürmek için|Yöntemi kullanın|  
|------------------|-------------------------------------|-------------------|  
|Dizin adları|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dizin bilgilerini (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Dosya adları|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya bilgileri (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş adları|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Dosya sistemi giriş bilgileri (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Dizin ve dosya adları |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> Kullanarak bir üst dizin dizinlerindeki tüm dosyaları hemen numaralandırabilirsiniz rağmen <xref:System.IO.SearchOption.AllDirectories> seçeneği isteğe bağlı <xref:System.IO.SearchOption> numaralandırma <xref:System.UnauthorizedAccessException> hata yapma sabit listesi eksik. İlk dizinleri numaralandırma ve ardından dosyaları numaralandırma bu özel durumları yakalayabilir.  
  
## <a name="examples-use-the-directory-class"></a>Örnekler: Dizin sınıfı kullanın  
  
Aşağıdaki örnekte <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> belirtilen yolda gidemez adlarının bir listesini almak için yöntemi.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Aşağıdaki örnekte <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> yöntemi için yinelemeli olarak bir dizin ve belirli bir desenle eşleşen alt dizinlerdeki tüm dosya adlarını numaralandırır. Her dosyanın her bir satır okur ve dosya adlarını ve yollarını belirtilen bir dizeyi içeren satırları gösterir.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Örnekler: DirectoryInfo sınıfı kullanın  
  
Aşağıdaki örnekte <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> yöntemi üst düzey dizinler koleksiyonu listelemek için <xref:System.IO.FileSystemInfo.CreationTimeUtc> bazı önceki <xref:System.DateTime> değeri.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Aşağıdaki örnekte <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> tüm listelemek için yöntemi dosyaları <xref:System.IO.FileInfo.Length> 10 MB'ı aşıyor. Bu örnekte, ilk olası yetkisiz erişim özel durumları yakalamak için üst düzey dizinleri numaralandırır ve ardından dosyaları listeler.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
