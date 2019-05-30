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
ms.openlocfilehash: 908ac7c441dbb7f6c70b9fafc701d403fc153222
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251082"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Azaltma: ZipArchiveEntry.FullName yol ayırıcısı
.NET Framework 4.6.1'i hedefleyen uygulamalar ile başlayarak, yol ayırıcı olarak kullanılan <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği, ters eğik çizgiden değişti ("\\") eğik çizgi ("/") için .NET Framework'ün önceki sürümlerinde kullanılan.   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> nesneleri, aşırı yüklemelerini çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="impact"></a>Etki  
 Değişiklik 4.4.17.1 bölümünü ile uyumu .NET uygulamasına getirir [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve sağlar. Windows olmayan sistemlerde sıkıştırmasının açılması için ZIP arşivlerini.  
  
 Dizin yapısı korumak için Macintosh gibi Windows olmayan işletim sistemlerinde .NET Framework'ün önceki bir sürümü başarısız hedefleyen bir uygulama tarafından oluşturulan bir zip dosyası açılıyor. Örneğin, bir dosya adı, dizin yolu bir eğik çizgi ile birlikte art arda ekler kümesini oluşturur Macintosh ("\\") karakteri ve dosya adı. Sonuç olarak, açılan sıkıştırılmış dosyaların dizin yapısını korunmaz.  
  
 Bu değişiklik etkisini. Windows işletim sisteminde .NET Framework API'leri tarafından sıkıştırması ZIP dosyaları <xref:System.IO> bu API'leri bir eğik çizgi ("/") veya ters eğik çizgi sorunsuz bir şekilde işleyebilir beri ad alanı en az olmalıdır ("\\") olarak yol ayırıcı karakteri.  
  
## <a name="mitigation"></a>Azaltma  
 Bu davranış, istenmeyen ise, / için bir yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyasının. Aşağıdaki her ikisini de gösteren `<runtime>` bölümü ve geri çevirme anahtar.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ayrıca, .NET Framework 4.6.1 ve sonraki sürümleri çalıştıran ancak .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar, bu davranışı için için bir yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) Uygulama yapılandırma dosyası bölümünü. Aşağıdaki her ikisini de gösteren `<runtime>` bölümü ve katılım anahtar.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [4.6.1 uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
