---
title: 'Azaltma: ZipArchiveEntry.FullName yol ayırıcısı'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3940cf8d1ebda668925a5c461b84a8bc61550476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391140"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Azaltma: ZipArchiveEntry.FullName yol ayırıcısı
Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], kullanılan yol ayırıcısı <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği, ters eğik çizgi değişti ("\\") bir eğik çizgi ("/") için .NET Framework'ün önceki sürümlerinde kullanılan.   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> nesneler aşırı birini çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="impact"></a>Etki  
 Değişiklik 4.4.17.1 bölümüne ile uygunluk .NET uygulamasına getirir [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve sağlar. Windows olmayan sistemlerde açılması için ZIP arşivler.  
  
 Dizin yapısı korumak için .NET Framework Windows olmayan işletim sistemlerinde Macintosh gibi önceki bir sürümünü başarısız hedefleyen bir uygulama tarafından oluşturulan bir zip dosyası açılıyor. Örneğin, dosya, dosya adı, dizin yolu bir eğik çizgi ile birlikte art arda ekler kümesi oluşturur Macintosh ("\\") karakterleri ve dosya adı. Sonuç olarak, açılan sıkıştırılmış dosyaların dizin yapısını korunmaz.  
  
 Bu değişiklik etkisi. .NET Framework API'leri tarafından Windows işletim sistemi sıkıştırması ZIP dosyaları <xref:System.IO> bu API'leri bir eğik çizgi ("/") veya ters eğik çizgi sorunsuz bir şekilde işleyebilir beri ad alanı en az olmalıdır ("\\") yol ayırıcı karakter olarak.  
  
## <a name="mitigation"></a>Azaltma  
 Bu davranış istenmeyen ise, dışında bir yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının. Aşağıdaki her ikisi de gösterir `<runtime>` bölümü ve vazgeçme anahtar.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak üzerinde çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme Bu davranışı için bir yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü Uygulama yapılandırma dosyası. Aşağıdaki her ikisi de gösterir `<runtime>` bölümü ve katılımı anahtar.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [4.6.1 uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
