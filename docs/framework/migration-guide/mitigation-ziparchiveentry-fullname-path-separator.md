---
title: 'Risk azaltma: ZipArchiveEntry. FullName yol ayırıcısı'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 495377403e2f0c0f5f4f166f51d738265c16ef7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126056"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Risk azaltma: ZipArchiveEntry. FullName yol ayırıcısı
.NET Framework 4.6.1 ' i hedefleyen uygulamalarla başlayarak, <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliğinde kullanılan yol ayırıcısı, önceki .NET Framework önceki sürümlerinde kullanılan ters eğik çizgiyle ("\\") değiştirilmiştir ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> nesneler, <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yönteminin aşırı yüklerinden biri çağırarak oluşturulur.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, .NET uygulamasını konusunun Bölüm 4.4.17.1 ile uyum sağlar [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve izin verir. ZIP arşivleri Windows dışı sistemlerde açılacak.  
  
 Macintosh gibi Windows dışı işletim sistemlerinde .NET Framework önceki bir sürümünü hedefleyen bir uygulama tarafından oluşturulan bir ZIP dosyasını açma işlemi, dizin yapısını koruyamaz. Örneğin, Macintosh üzerinde, dosya adı dizin yolunu, herhangi bir ters eğik çizgi ("\\") karakteri ve dosya adı ile birleştiren bir dosya kümesi oluşturur. Sonuç olarak, açılan dosyaların dizin yapısı korunmaz.  
  
 Bu değişikliğin üzerinde etkisi. Windows işletim sisteminde .NET Framework <xref:System.IO> ad alanındaki API 'Ler tarafından açılan ZIP dosyaları en düşük düzeyde olmalıdır, çünkü bu API 'Ler yol ayırıcı karakteri olarak eğik çizgi ("/") veya ters eğik çizgi ("\\") gibi sorunsuz bir şekilde işleyebilir.  
  
## <a name="mitigation"></a>Azaltma  
 Bu davranış istenmeyen bir durum ise, uygulama yapılandırma dosyanızın [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne bir yapılandırma ayarı ekleyerek devre dışı bırakabilirsiniz. Aşağıda hem `<runtime>` bölümü hem de geri çevirme anahtarı gösterilmektedir.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, uygulamanın [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne bir yapılandırma ayarı ekleyerek bu davranışı kabul edebilir yapılandırma dosyası. Aşağıda hem `<runtime>` bölümü hem de kabul etme anahtarı gösterilmektedir.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6-1.md)
- [4.6.1 'de uygulama uyumluluğu](application-compatibility-in-the-net-framework-4-6-1.md)
