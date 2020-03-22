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

Aşağıdaki tablolarda .NET Framework dosyası G/Ç için yaygın olarak kullanılan, dosya G/Ç sınıflarına kategorize edilen sınıflar, akış oluşturmak için kullanılan sınıflar ve akışlara okuma ve yazma için kullanılan sınıflar listelenebiledir.  
  
Daha kapsamlı bir giriş için [Sınıf Kitaplığı Genel Bakış'a](../../../../standard/class-library-overview.md)bakın.  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Dosyalar, Sürücüler ve Dizinler için Temel G/Ç Sınıfları  

 Aşağıdaki tablo listeler ve dosya G/Ç için kullanılan ana sınıfları açıklar.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve derecelendirme için statik yöntemler sağlar.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve derecelendirme için örnek yöntemleri sağlar.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Sürücüler arasında oluşturma, taşıma ve derecelendirme için örnek yöntemleri sağlar.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Dosyaları oluşturmak, kopyalamak, silerken, taşımak ve açmak için statik yöntemler `FileStream`sağlar ve bir .|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Bir dosyaya okuma, yazma veya okuma/yazma erişimi için sabitleri tanımlar.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|, , `Archive` `Hidden`ve . gibi dosyalar `ReadOnly`ve dizinler için öznitelikleri sağlar.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Dosyaları oluşturmak, kopyalamak, silerken, taşımak ve açmak için statik yöntemler `FileStream`sağlar ve bir .|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Dosyanın nasıl açıldığını denetler. Bu parametre için ve , ve `FileStream` `IsolatedStorageFileStream` `Open` yöntemleri <xref:System.IO.File> <xref:System.IO.FileInfo>için ve .|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Diğer dosya akışlarının aynı dosyaya sahip olabileceği erişim türünü denetlemek için sabitleri tanımlar.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|İşleme dizini dizeleri için yöntem ve özellikler sağlar.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Dosyalarıve klasörleri <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> ve <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> izinleri tanımlayarak denetler.|  
  
## <a name="classes-used-to-create-streams"></a>Akış Oluşturmak için Kullanılan Sınıflar  

 Aşağıdaki tablo listeler ve akışları oluşturmak için kullanılan ana sınıfları açıklar.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Başka bir akışta işlemleri okumak ve yazmak için bir arabellek katmanı ekler.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<xref:System.IO.FileStream.Seek%2A> Kendi yöntemi yle dosyalara rasgele erişimi destekler. <xref:System.IO.FileStream>dosyaları varsayılan olarak eşzamanlı olarak açar, ancak eşzamanlı işlemi de destekler.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Bir dosya yerine destek deposu bellek olan bir akış oluşturur.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Ağ erişimi için temel veri akışını sağlar.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Veri akışlarını şifreleme dönüşümlerine bağlayan bir akış tanımlar.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Akışlardan Okumak ve Yazmak Için Kullanılan Sınıflar  

 Aşağıdaki tablo, akışlı dosyalara okuma ve yazma için kullanılan belirli sınıfları gösterir.  
  
|**Sınıf**|**Açıklama**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Kodlanmış dizeleri ve ilkel veri <xref:System.IO.FileStream>türlerini bir .|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Kodlanmış dizeleri ve ilkel veri <xref:System.IO.FileStream>türlerini bir ' ye yazar.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Karakterleri baytlara <xref:System.IO.FileStream>dönüştürmek <xref:System.IO.StreamReader.CurrentEncoding%2A> için kullanarak a'daki karakterleri okur. <xref:System.IO.StreamReader>bayt sıraişareti gibi belirli bir <xref:System.IO.StreamReader.CurrentEncoding%2A> <xref:System.IO.StreamReader.CurrentEncoding%2A>önsözün varlığına bağlı olarak belirli bir akış için doğrutespitiyapmaya çalışan bir oluşturucuya sahiptir.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Karakterleri baytlara `FileStream`dönüştürmek <xref:System.IO.StreamWriter.Encoding%2A> için kullanarak karakterleri a'ya yazar.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Karakterleri bir `String`' den okur. Çıktı herhangi bir kodlama da bir `String`akış veya bir .|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Karakterleri yazar. `String` Çıktı herhangi bir kodlama da bir `String`akış veya bir .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)
- [Dosya ve Akış G/Ç'si](../../../../standard/io/index.md)
- [Zaman Uyumsuz Dosya G/Ç](../../../../standard/io/asynchronous-file-i-o.md)
- [Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
