---
title: Ortak G/Ç Görevleri
description: .NET 'teki System.IO ad alanındaki sınıflar & yöntemleri kullanarak ortak dizin görevlerini & ortak dosya görevlerinin nasıl yapılacağını öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 4b97b4e464622e482a9ef45e143865ee82e6b5d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598612"
---
# <a name="common-io-tasks"></a>Ortak G/Ç Görevleri
<xref:System.IO>Ad alanı, dosyalar, dizinler ve akışlar üzerinde gerçekleştirilen okuma ve yazma gibi çeşitli eylemlere izin veren birkaç sınıf sağlar. Daha fazla bilgi için bkz. [dosya ve akış g/ç](index.md).  
  
## <a name="common-file-tasks"></a>Yaygın Dosya Görevleri  
  
|Bunu yapmak için...|Bu konudaki örneğe bakın...|  
|-------------------|--------------------------------------|  
|Bir metin dosyası oluşturma|<xref:System.IO.File.CreateText%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.File.Create%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType> yöntemi|  
|Bir metin dosyasına yazma|[Nasıl yapılır: Bir Dosyaya Metin Yazma](how-to-write-text-to-a-file.md)<br /><br /> [Nasıl yapılır: Metin Dosyaları Yazma (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Bir metin dosyasından okuma|[Nasıl yapılır: Dosyadan Metin Okuma](how-to-read-text-from-a-file.md)|  
|Bir dosyaya metin ekleme|[Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme](how-to-open-and-append-to-a-log-file.md)<br /><br /> <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyayı yeniden adlandırma veya taşıma|<xref:System.IO.File.Move%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType> yöntemi|  
|Dosyayı silme|<xref:System.IO.File.Delete%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyayı kopyalama|<xref:System.IO.File.Copy%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyanın boyutunu alma|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>özelliði|  
|Bir dosyanın özniteliklerini alma|<xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyanın özniteliklerini ayarlama|<xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyanın var olup olmadığını belirleme|<xref:System.IO.File.Exists%2A?displayProperty=nameWithType> yöntemi|  
|Bir ikili dosyadan okuma|[Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Bir ikili dosyaya yazma|[Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Bir dosya adı uzantısını alma|<xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyanın tam yolunu alma|<xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> yöntemi|  
|Bir yoldan dosya adını ve uzantısını alma|<xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType> yöntemi|  
|Bir dosyanın uzantısını değiştirme|<xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType> yöntemi|  
  
## <a name="common-directory-tasks"></a>Yaygın Dizin Görevleri  
  
|Bunu yapmak için...|Bu konudaki örneğe bakın...|  
|-------------------|--------------------------------------|  
|Belgelerim gibi özel bir klasördeki bir dosyaya erişme|[Nasıl yapılır: Bir Dosyaya Metin Yazma](how-to-write-text-to-a-file.md)|  
|Dizin oluşturma|<xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>özelliði|  
|Bir alt dizin oluşturma|<xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType> yöntemi|  
|Bir dizini yeniden adlandırma veya taşıma|<xref:System.IO.Directory.Move%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType> yöntemi|  
|Bir dizini kopyalama|[Nasıl yapılır: Dizinleri Kopyalama](how-to-copy-directories.md)|  
|Bir dizini silme|<xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType> yöntemi<br /><br /> <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType> yöntemi|  
|Bir dizindeki dosyaları ve alt dizinleri görme|[Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma](how-to-enumerate-directories-and-files.md)|  
|Bir dizinin boyutunu bulma|<xref:System.IO.Directory?displayProperty=nameWithType> sınıfı|  
|Bir dizinin var olup olmadığını belirleme|<xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType> yöntemi|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve akış g/ç](index.md)
- [Akışlar Oluşturma](composing-streams.md)
- [Zaman uyumsuz dosya g/ç](asynchronous-file-i-o.md)
