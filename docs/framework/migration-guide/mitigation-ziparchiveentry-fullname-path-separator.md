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
ms.openlocfilehash: eba871215f33e4d3b50054e9ceaa92be090d0143
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125113"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Azaltma: ZipArchiveEntry.FullName yol ayırıcısı
Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], kullanılan yolu ayırıcısı <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği, ters eğik çizgiden değişti ("\\") eğik çizgi ("/") için .NET Framework'ün önceki sürümlerinde kullanılan.   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> nesneleri, aşırı yüklemelerini çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yöntemi.  
  
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
  
 Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak üzerinde çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme için bu davranışı için bir yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü Uygulama yapılandırma dosyası. Aşağıdaki her ikisini de gösteren `<runtime>` bölümü ve katılım anahtar.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [4.6.1 uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
