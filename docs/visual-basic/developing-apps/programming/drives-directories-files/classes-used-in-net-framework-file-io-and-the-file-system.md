---
title: Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: fe70f8fb655579049bb36fc324d04530259d25f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348925"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar (Visual Basic)

Aşağıdaki tablolarda, .NET Framework dosya g/ç için yaygın olarak kullanılan sınıflar, dosya g/ç sınıfları, akış oluşturmak için kullanılan sınıflar ve akışlarda okuma ve yazma için kullanılan sınıflar listelenmektedir.  
  
Daha kapsamlı bir liste için bkz. [sınıf kitaplığına genel bakış](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Dosyalar, sürücüler ve dizinler için temel g/ç sınıfları  

 Aşağıdaki tabloda dosya g/ç için kullanılan ana sınıflar listelenmektedir ve açıklanmaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve sıralama için statik yöntemler sağlar.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve numaralandırma için örnek yöntemleri sağlar.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Sürücüler arasında oluşturma, taşıma ve numaralandırma için örnek yöntemleri sağlar.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Dosya oluşturma, kopyalama, silme, taşıma ve açma için statik yöntemler sağlar ve a `FileStream`'nın oluşturulmasına yardımcı olur.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Bir dosyaya okuma, yazma veya okuma/yazma erişimi için sabitleri tanımlar.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|`Archive`, `Hidden`Ve `ReadOnly`gibi dosyalar ve dizinler için öznitelikler sağlar.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Dosya oluşturma, kopyalama, silme, taşıma ve açma için statik yöntemler sağlar ve a `FileStream`'nın oluşturulmasına yardımcı olur.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Bir dosyanın nasıl açıldığını denetler. Bu parametre `FileStream` `IsolatedStorageFileStream`, ve için ve `Open` yöntemleri <xref:System.IO.File> için ve için oluşturucuların çoğunda belirtilir. <xref:System.IO.FileInfo>|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Diğer dosya akışlarının aynı dosyaya sahip olduğu erişimin türünü denetlemek için sabitleri tanımlar.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Dizin dizelerini işlemek için yöntemler ve özellikler sağlar.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|, <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> Ve izinleri tanımlayarak dosya ve klasörlerin erişimini <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> denetler.|  
  
## <a name="classes-used-to-create-streams"></a>Akış oluşturmak için kullanılan sınıflar  

 Aşağıdaki tabloda, akışlar oluşturmak için kullanılan ana sınıflar listelenmektedir ve açıklanmaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Başka bir akışta okuma ve yazma işlemlerine yönelik bir arabelleğe alma katmanı ekler.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|, <xref:System.IO.FileStream.Seek%2A> Yöntemi aracılığıyla dosyalara rastgele erişimi destekler. <xref:System.IO.FileStream>dosyaları varsayılan olarak eşzamanlı olarak açar, ancak aynı zamanda zaman uyumsuz işlemi destekler.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Yedekleme deposu bir dosya yerine bellek olan bir akış oluşturur.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Ağ erişimi için temel alınan veri akışını sağlar.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Veri akışlarını şifreleme dönüşümlerine bağlayan bir akış tanımlar.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Akışları okumak ve akışlara yazmak için kullanılan sınıflar  

 Aşağıdaki tabloda, akışlarla dosyaları okumak ve dosyalara yazmak için kullanılan belirli sınıflar gösterilmektedir.  
  
|**Sınıfı**|**Açıklama**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Bir <xref:System.IO.FileStream>öğesinden kodlanmış dizeleri ve temel veri türlerini okur.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Kodlanmış dizeleri ve temel veri türlerini bir <xref:System.IO.FileStream>öğesine yazar.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Karakterleri, bayttan ve <xref:System.IO.FileStream>baytlara <xref:System.IO.StreamReader.CurrentEncoding%2A> dönüştürmek için kullanarak bir öğesinden okur. <xref:System.IO.StreamReader>, belirli bir akış için, bayt sırası işareti gibi belirli <xref:System.IO.StreamReader.CurrentEncoding%2A> bir <xref:System.IO.StreamReader.CurrentEncoding%2A>girişin varolup olmadığını belirlemek için doğru yokuna izin veren bir oluşturucuya sahiptir.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Karakteri bayta dönüştürmek için `FileStream`bir, <xref:System.IO.StreamWriter.Encoding%2A> kullanarak karakter yazar.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|İçindeki karakterleri okur `String`. Çıkış herhangi bir kodlamada veya bir `String`akışta akış olabilir.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|' A `String`karakter yazar. Çıkış herhangi bir kodlamada veya bir `String`akışta akış olabilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)
- [Dosya ve akış g/ç](../../../../standard/io/index.md)
- [Zaman uyumsuz dosya g/ç](../../../../standard/io/asynchronous-file-i-o.md)
- [Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
