---
title: 'Azaltma: ZipArchiveEntry.FullName Yol Ayırıcı'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457725"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Azaltma: ZipArchiveEntry.FullName Yol Ayırıcı
.NET Framework 4.6.1'i hedefleyen uygulamalardan başlayarak, <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özellikte kullanılan yol ayırıcısı .NET Framework'ün önceki sürümlerinde kullanılan ters eğik çizgiden ("/")\\ileri eğik çizgiye ("/") dönüşmüştür.   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType><xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> nesneler, yöntemin aşırı yüklerinden birini çağırarak oluşturulur.  
  
## <a name="impact"></a>Etki  
 Değişiklik, .NET uygulamasını 4.4.17.1 bölümüne uygun bir şekilde [getirir. ZIP Dosya Formatı Belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve sağlar. Windows olmayan sistemlerde sıkıştırılacak ZIP arşivleri.  
  
 Macintosh gibi Windows dışı işletim sistemlerinde .NET Framework'ün önceki bir sürümünü hedefleyen bir uygulama tarafından oluşturulan zip dosyasını sıkıştırmak dizin yapısını koruyamaz. Örneğin, Macintosh'ta, dosya adı dizin yolunu, herhangi bir ters eğik çizgi ("\\") karakterle ve dosya adıyla birlikte birleştirir. Sonuç olarak, sıkıştırılmış dosyaların dizin yapısı korunmaz.  
  
 Bu değişikliğin . .NET Framework <xref:System.IO> ad alanında API'ler tarafından Windows işletim sisteminde sıkıştırılan ZIP dosyaları en az düzeyde olmalıdır, çünkü bu API'ler yol\\ayırıcı karakteri olarak bir eğik çizgi ("/") veya ters eğik çizgi (" ") sorunsuz bir şekilde işleyebilir.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bu davranış istenmiyorsa, uygulama yapılandırma dosyanızın [ \<çalışma>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne yapılandırma ayarı ekleyerek devre dışı kullanabilirsiniz. Aşağıda hem `<runtime>` bölümü hem de devre dışı bırakma anahtarı nı gösterilmektedir.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, [ \<](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının çalışma zamanı>bölümüne yapılandırma ayarını ekleyerek bu davranışı seçebilir. Aşağıdaki bölüm ve `<runtime>` opt-in anahtarı hem de gösterir.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6-1.md)
- [Uygulama uyumluluğu](application-compatibility.md)
