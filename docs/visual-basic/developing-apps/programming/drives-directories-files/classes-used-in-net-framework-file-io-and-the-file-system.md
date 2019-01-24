---
title: Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: 9e84ac90054e4ac3d32bb436fc0756248e84fcd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705329"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar (Visual Basic)
.NET Framework dosyası g/ç, dosya g/ç sınıfları, akışları oluşturmak için kullanılan sınıfları ve okuma ve akışlara yazmak için kullanılan sınıfları kategorilere için yaygın olarak kullanılan sınıfları aşağıdaki tablolarda listelenmiştir.  
  
 Girmek için [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] belgelere ve Bul daha kapsamlı bir liste bakın [sınıf kitaplığına genel bakış](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Dosyalar, sürücüler ve dizinler için temel bir g/ç sınıfları  
 Aşağıdaki tabloda, listeler ve dosya g/ç için kullanılan temel sınıflar açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Oluşturma, taşıma ve dizinler ile alt dizinleri numaralandırma için statik yöntemler sağlar.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Oluşturma, taşıma ve dizinler ile alt dizinleri numaralandırma için örnek yöntemleri sağlar.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Oluşturma, taşıma ve sürücüler numaralandırma için örnek yöntemleri sağlar.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Oluşturma, kopyalama, silme, taşıma ve dosya açma için statik yöntemler sağlar ve kolaylık sağlar, oluşturma sırasında bir `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Okuma, yazma ya da bir dosya için okuma/yazma erişimi sabitleri tanımlar.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Dosyalar ve dizinler için öznitelikleri gibi sağlar `Archive`, `Hidden`, ve `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Oluşturma, kopyalama, silme, taşıma ve dosya açma için statik yöntemler sağlar ve kolaylık sağlar, oluşturma sırasında bir `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Bir dosyanın nasıl açıldığı denetler. Bu parametre için oluşturucular birçok belirtilen `FileStream` ve `IsolatedStorageFileStream`ve `Open` yöntemlerinin <xref:System.IO.File> ve <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Diğer dosya akışları aynı dosyada olabilir erişim türünü denetleme sabitlerini tanımlar.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Dizin dizeleri işlemek için yöntemler ve özellikler sağlar.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Tanımlayarak dosya ve klasörlerin erişim denetimleri <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> ve <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> izinleri.|  
  
## <a name="classes-used-to-create-streams"></a>Akışlar oluşturmak üzere kullanılan sınıflar  
 Aşağıdaki tabloda, listeler ve akışlar oluşturmak üzere kullanılan ana sınıfları açıklar.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Okuma ve yazma işlemi başka bir akış için arabelleğe alma katmanı ekler.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Rastgele erişim aracılığıyla dosyaları destekler, <xref:System.IO.FileStream.Seek%2A> yöntemi. <xref:System.IO.FileStream> dosyalar varsayılan olarak zaman uyumlu olarak açılır. ancak zaman uyumsuz işlem de destekler.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Yedekleme deposu ayarlanmış olan bir dosya yerine belleği olan bir akış oluşturur.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Temel alınan veri akışını ağ erişim sağlar.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Veri akışlarını şifreleme dönüştürmelerine bağlanan bir akışı tanımlar.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Okuma ve akışlara yazmak için kullanılan sınıflar  
 Aşağıdaki tabloda, akışları ile dosyalara yazma ve okuma için kullanılan belirli sınıflarını göstermektedir.  
  
|**Sınıfı**|**Açıklama**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Kodlanmış dizeleri ve temel veri türlerinden okuyan bir <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Kodlanmış dizeleri ve basit veri türleri için yazar bir <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Karakterleri okur bir <xref:System.IO.FileStream>kullanarak <xref:System.IO.StreamReader.CurrentEncoding%2A> karakterleri için ve baytlardan dönüştürmek için. <xref:System.IO.StreamReader> doğru anlamamıza çalışır bir oluşturucusu vardır <xref:System.IO.StreamReader.CurrentEncoding%2A> belirli bir akış için varlığına dayalı bir <xref:System.IO.StreamReader.CurrentEncoding%2A>-bayt sırası işareti gibi belirli bir giriş.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Karakterler için yazar bir `FileStream`kullanarak <xref:System.IO.StreamWriter.Encoding%2A> bayt karakterlerini dönüştürmek için.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Karakterleri okur bir `String`. Çıkış kodlaması herhangi bir ya da akış olabilir veya `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Karakterler için yazar bir `String`. Çıkış kodlaması herhangi bir ya da akış olabilir veya `String`.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)
- [Dosya ve Akış G/Ç'si](../../../../standard/io/index.md)
- [Zaman Uyumsuz Dosya G/Ç](../../../../standard/io/asynchronous-file-i-o.md)
- [.NET Framework dosyası g/ç ve dosya sistemi (Visual Basic) hakkında temel bilgiler](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
