---
title: 'Risk azaltma: ZipArchiveEntry. FullName yol ayırıcısı'
description: ZipArchiveEntry. FullName özelliği için yol ayırıcısının, .NET Framework 4.6.1 hedeflenen uygulamalarla başlayarak nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475300"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Risk azaltma: ZipArchiveEntry. FullName yol ayırıcısı

.NET Framework 4.6.1 ' i hedefleyen uygulamalarla başlayarak, özellikte kullanılan yol ayırıcısı, <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> \\ önceki .NET Framework sürümlerinde kullanılan ters eğik çizgiyle ("") ("/") değiştirilmiştir. <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>nesneler, yönteminin aşırı yüklerinden biri çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> .  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, .NET uygulamasını konusunun Bölüm 4.4.17.1 ile uyum sağlar [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve izin verir. ZIP arşivleri Windows dışı sistemlerde açılacak.  
  
 MacOS gibi Windows dışı işletim sistemlerinde .NET Framework önceki bir sürümünü hedefleyen, dizin yapısını koruyamayan bir uygulama tarafından oluşturulan bir zip dosyasını açma işlemi başarısız oluyor. Örneğin, MacOS 'ta dosya adı dizin yolunu, herhangi bir ters eğik çizgi (" \\ ") karakterini ve dosya adını birleştiren bir dosya kümesi oluşturur. Sonuç olarak, açılan dosyaların dizin yapısı korunmaz.  
  
 Bu değişikliğin üzerinde etkisi. <xref:System.IO>Bu API 'ler, yol ayırıcı karakteri olarak eğik çizgi ("/") veya ters eğik çizgi ("") ile sorunsuz bir şekilde işleyebildiğinden, Windows işletim sisteminde .NET Framework API 'ler tarafından AÇıLAN ZIP dosyaları en az olmalıdır \\ .  
  
## <a name="mitigation"></a>Risk azaltma  
 Bu davranış istenmeyen bir durum ise, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne bir yapılandırma ayarı ekleyerek devre dışı bırakabilirsiniz. Aşağıda hem `<runtime>` bölümü hem de geri çevirme anahtarı gösterilmektedir.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ayrıca, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının bölümüne bir yapılandırma ayarı ekleyerek bu davranışı kabul edebilir. Aşağıda hem `<runtime>` bölümü hem de kabul etme anahtarı gösterilmektedir.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
