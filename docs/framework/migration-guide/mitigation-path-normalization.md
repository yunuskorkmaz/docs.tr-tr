---
title: 'Azaltma: Yol Normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181231"
---
# <a name="mitigation-path-normalization"></a>Azaltma: Yol Normalleştirme
.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak,.NET Framework'deki yol normalleştirmesi değişti.  
  
## <a name="what-is-path-normalization"></a>Yol normalleştirme nedir?  
 Bir yolu normalleştirmek, hedef işletim sistemindegeçerli bir yola uyacak şekilde bir yolu veya dosyayı tanımlayan dizeyi değiştirmeyi içerir. Normalleştirme genellikle içerir:  
  
- Bileşen ve dizin ayırıcıları canonicalizing.  
  
- Geçerli dizini göreli bir yola uygulama.  
  
- Bir yolda göreli`.`dizinin ( ) veya`..`üst dizinin değerlendirilmesi.  
  
- Belirtilen karakterleri kırpma.  
  
## <a name="the-changes"></a>Değişiklikler  
 .NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak yol normalleştirmesi aşağıdaki şekillerde değişti:  
  
- Çalışma süresi, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) işlevine erteler.  
  
- Normalleştirme artık dizin kesimlerinin sonunda (dizin adının sonundaki boşluk gibi) kırpmayı içermez.  
  
- Aygıt yolu sözdizimini tam `\\.\` güven içinde ve mscorlib.dll'deki `\\?\`dosya G/Ç API'leri için destek.  
  
- Çalışma zamanı aygıt sözdizimi yollarını doğrulamaz.  
  
- Alternatif veri akışlarına erişmek için aygıt sözdizimi kullanımı desteklenir.  
  
## <a name="impact"></a>Etki  

.NET Framework 4.6.2 veya sonraki lerini hedefleyen uygulamalar için bu değişiklikler varsayılan olarak açıktır. Yöntemlerin daha önce erişilemeyen yollara erişmesine izin verirken performansı artırmaları gerekir.  
  
.NET Framework 4.6.1 ve önceki sürümleri hedefleyen ancak .NET Framework 4.6.2 veya daha sonra ları altında çalışan uygulamalar bu değişiklikten etkilenmez.  
  
## <a name="mitigation"></a>Risk azaltma  
 .NET Framework 4.6.2 veya daha sonrasını hedefleyen uygulamalar bu değişikliği devre dışı bırakıp [ \<](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının çalışma süresi>bölümüne aşağıdakileri ekleyerek eski normalleştirmeyi kullanabilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
.NET Framework 4.6.1 veya daha öncesini hedefleyen ancak .NET Framework 4.6.2 veya sonraki bölümlerinde çalışan uygulamalar, uygulamanın [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek normalize yol değişikliklerini etkinleştirebilir .configuration dosyası:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
