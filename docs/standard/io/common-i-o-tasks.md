---
title: Ortak G/Ç Görevleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf0caa0513881d5a1096478d8b29fc708ac3d3ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577661"
---
# <a name="common-io-tasks"></a>Ortak G/Ç Görevleri
<xref:System.IO> Ad alanı akışları ve okuma ve yazma dizinleri, dosyaları üzerinde gerçekleştirilecek gibi çeşitli eylemler için izin birkaç sınıfları sağlar. Daha fazla bilgi için bkz: [dosya ve akış g/ç](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Yaygın Dosya Görevleri  
  
|Bunu yapmak için...|Bu konudaki örneğe bakın...|  
|-------------------|--------------------------------------|  
|Bir metin dosyası oluşturma|<xref:System.IO.File.CreateText%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.File.Create%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType> Yöntemi|  
|Bir metin dosyasına yazma|[Nasıl yapılır: Bir Dosyaya Metin Yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Nasıl yapılır: Metin Dosyaları Yazma (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Bir metin dosyasından okuma|[Nasıl yapılır: Dosyadan Metin Okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Bir dosyaya metin ekleme|[Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyayı yeniden adlandırma veya taşıma|<xref:System.IO.File.Move%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyayı silme|<xref:System.IO.File.Delete%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyayı kopyalama|<xref:System.IO.File.Copy%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyanın boyutunu alma|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType> Özelliği|  
|Bir dosyanın özniteliklerini alma|<xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyanın özniteliklerini ayarlama|<xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyanın var olup olmadığını belirleme|<xref:System.IO.File.Exists%2A?displayProperty=nameWithType> Yöntemi|  
|Bir ikili dosyadan okuma|[Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Bir ikili dosyaya yazma|[Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Bir dosya adı uzantısını alma|<xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyanın tam yolunu alma|<xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> Yöntemi|  
|Bir yoldan dosya adını ve uzantısını alma|<xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dosyanın uzantısını değiştirme|<xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType> Yöntemi|  
  
## <a name="common-directory-tasks"></a>Yaygın Dizin Görevleri  
  
|Bunu yapmak için...|Bu konudaki örneğe bakın...|  
|-------------------|--------------------------------------|  
|Belgelerim gibi özel bir klasördeki bir dosyaya erişme|[Nasıl yapılır: Bir Dosyaya Metin Yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Bir dizin oluşturma|<xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType> Özelliği|  
|Bir alt dizin oluşturma|<xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dizini yeniden adlandırma veya taşıma|<xref:System.IO.Directory.Move%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dizini kopyalama|[Nasıl yapılır: Dizinleri Kopyalama](../../../docs/standard/io/how-to-copy-directories.md)|  
|Bir dizini silme|<xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType> Yöntemi<br /><br /> <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType> Yöntemi|  
|Bir dizindeki dosyaları ve alt dizinleri görme|[Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Bir dizinin boyutunu bulma|<xref:System.IO.Directory?displayProperty=nameWithType> sınıfı|  
|Bir dizinin var olup olmadığını belirleme|<xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType> Yöntemi|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)  
 [Akışlar Oluşturma](../../../docs/standard/io/composing-streams.md)  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)
