---
title: "Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08fd340e895376b43f95a767992ef0d3c0c819c6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar (Visual Basic)
Aşağıdaki tablolarda, .NET Framework dosyası g/ç, dosya g/ç sınıfları, akışları oluşturmak için kullanılan sınıfları ve okuma ve akışlara yazmak için kullanılan sınıfları içine kategorilere için yaygın olarak kullanılan sınıflar listelenir.  
  
 Girmek için [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] belgelere ve Bul daha kapsamlı bir liste bakın [sınıf kitaplığına genel bakış](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Dosyalar, sürücüler ve dizinler için temel g/ç sınıfları  
 Aşağıdaki tabloda listelenmekte ve dosya g/ç için kullanılan ana sınıflar açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Oluşturma, taşıma ve dizin ve alt dizinlere numaralandırma için statik yöntemler sağlar.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Oluşturma, taşıma ve dizin ve alt dizinlere numaralandırma için örnek yöntemleri sağlar.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Oluşturma, taşıma ve sürücüler numaralandırma için örnek yöntemleri sağlar.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Oluşturma, kopyalama, silme, taşıma ve dosyaları açma için statik yöntemler sağlar ve yardımları yılında bir `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Okuma, yazma ya da bir dosyaya okuma/yazma erişimi sabitleri tanımlar.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Dosyalar ve dizinler için öznitelikleri gibi sağlar `Archive`, `Hidden`, ve `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Oluşturma, kopyalama, silme, taşıma ve dosyaları açma için statik yöntemler sağlar ve yardımları yılında bir `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Bir dosyayı nasıl açıldığı denetler. Bu parametre oluşturucuları için birçoğunu belirtildiğinden `FileStream` ve `IsolatedStorageFileStream`ve `Open` yöntemlerinin <xref:System.IO.File> ve <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Diğer dosya akışlar aynı dosyaya olabilir erişim türünü denetlemek için sabitleri tanımlar.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Dizin dizeleri işlemek için yöntemleri ve özellikleri sağlar.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Tanımlayarak dosyalara ve klasörlere erişim denetimleri <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> ve <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> izinleri.|  
  
## <a name="classes-used-to-create-streams"></a>Akışlar oluşturmak üzere kullanılan sınıflar  
 Aşağıdaki tabloda listelenmekte ve akışlar oluşturmak üzere kullanılan ana sınıflar açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Okuma ve yazma işlemlerini başka bir akış üzerinde için arabelleğe alma katmanı ekler.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Dosyalar ile rastgele erişim destekler, <xref:System.IO.FileStream.Seek%2A> yöntemi. <xref:System.IO.FileStream>dosyaları zaman uyumlu olarak varsayılan olarak açar ancak zaman uyumsuz işlemi de destekler.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Bir dosya yerine, bellek, yedekleme deposudur bir akış oluşturur.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Temel alınan veri akışı için ağ erişimi sağlar.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Veri akışları için şifreleme dönüştürmeleri bağlanan bir akış tanımlar.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Okuma ve akışlara yazmak için kullanılan sınıfları  
 Aşağıdaki tabloda, okuma ve dosyalara akışlarla yazmak için kullanılan belirli sınıfları gösterir.  
  
|**Sınıfı**|**Açıklama**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Kodlanmış dizeler ve temel veri türlerinden okuyan bir <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Kodlanmış dizeler ve temel veri türleri için yazar bir <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Karakterlerinden okuyan bir <xref:System.IO.FileStream>kullanarak <xref:System.IO.StreamReader.CurrentEncoding%2A> karakterlerini bayt gelen ve giden dönüştürmek için. <xref:System.IO.StreamReader>doğru onaylaması girişiminde kurucusunun <xref:System.IO.StreamReader.CurrentEncoding%2A> belirli bir akış için temel varlığı üzerinde bir <xref:System.IO.StreamReader.CurrentEncoding%2A>-bayt sırası işareti gibi belirli giriş.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Karakter Yazar bir `FileStream`kullanarak <xref:System.IO.StreamWriter.Encoding%2A> bayt karakter dönüştürülecek.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Karakterlerinden okuyan bir `String`. Çıktı kodlamada herhangi bir ya da akış olabilir veya bir `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Karakter Yazar bir `String`. Çıktı kodlamada herhangi bir ya da akış olabilir veya bir `String`.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)  
 [Dosya ve Akış G/Ç'si](../../../../standard/io/index.md)  
 [Zaman Uyumsuz Dosya G/Ç](../../../../standard/io/asynchronous-file-i-o.md)  
 [.NET Framework dosyası g/ç ve dosya sistemi (Visual Basic) Temelleri](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
