---
title: 'Azaltma: Yol normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1c704113c8e05e493cdb3ef24f6376ab54b1cb
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251121"
---
# <a name="mitigation-path-normalization"></a>Azaltma: Yol normalleştirme
Hedef .NET Framework 4.6.2 uygulamaları ile başlayarak, .NET Framework'teki yolu normalleştirme değişti.  
  
## <a name="what-is-path-normalization"></a>Yol normalleştirme nedir?  
 Bir yol normalleştirme, böylece geçerli bir yol hedef işletim sisteminde uyan bir yol veya dosya tanımlayan dize değiştirme içerir. Normalleştirme genellikle içerir:  
  
- Bileşen ve dizin ayırıcı standart hale getirme.  
  
- Geçerli dizine göreli bir yol uygulanıyor.  
  
- Göreli dizini değerlendirme (`.`) veya bir üst dizin (`..`) bir yolda.  
  
- Karakterleri kırpma belirtilmiş.  
  
## <a name="the-changes"></a>Değişiklikleri  
 .NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, aşağıdaki yollarla yolu normalleştirme değişmiştir:  
  
- İşletim sistemi için çalışma zamanı erteler [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) yolları'leri normalleştirmek için işlevi.  
  
- Artık normalleştirme directory Segment (örneğin, bir dizin adı, sonunda boşluk) sonuna kırpma içerir.  
  
- Cihaz yolu sözdizimi tam güven için destek dahil olmak üzere `\\.\` ve dosya g/ç API'leri mscorlib.dll için `\\?\`.  
  
- Çalışma zamanı, cihaz sözdizimi yolları doğrulamaz.  
  
- Alternatif veri akışları erişmek için cihaz sözdizimi desteklenmiyor.  
  
## <a name="impact"></a>Etki  

.NET Framework 4.6.2'yi hedefleyen uygulamalar için veya daha sonra bu değişiklikleri varsayılan olarak etkindir. Daha önce erişilemeyen yolları erişmek yöntemleri sağlarken performansı.  
  
.NET Framework 4.6.1 ve önceki sürümleri hedefleyen, ancak .NET Framework 4.6.2 altında çalışan ya da üzeri olan uygulamalar, bu değişiklikten etkilenmez.  
  
## <a name="mitigation"></a>Azaltma  
 Daha sonra bu dışında seçebilirsiniz veya .NET Framework 4.6.2'yi hedefleyen uygulamalar değiştirin ve aşağıdaki ekleyerek eski normalleştirme kullanın [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyası bölümünü:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
.NET Framework 4.6.1 veya önceki ancak hedefleyen uygulamaları .NET Framework 4.6.2 üzerinde çalışıyor veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü uygulama .configuration dosyası:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
