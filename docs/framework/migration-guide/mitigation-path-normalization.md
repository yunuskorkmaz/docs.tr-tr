---
title: 'Risk azaltma: yol normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 1e7b540975b84320d099ca004df5b6a87aa60f6a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457892"
---
# <a name="mitigation-path-normalization"></a>Risk azaltma: yol normalleştirme
Uygulamalarla başlayarak .NET Framework 4.6.2 hedefini hedefleyin .NET Framework yol normalleştirme değişmiştir.  
  
## <a name="what-is-path-normalization"></a>Yol normalleştirme nedir?  
 Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir. Normalleştirme genellikle şunları içerir:  
  
- Standart hale getirme bileşeni ve Dizin ayırıcıları.  
  
- Geçerli dizin göreli bir yola uygulanıyor.  
  
- Göreli dizin (`.`) veya üst dizin (`..`) bir yolda değerlendiriliyor.  
  
- Belirtilen karakterler kırpılırken.  
  
## <a name="the-changes"></a>Değişiklikler  
 .NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirme aşağıdaki yollarla değiştirilmiştir:  
  
- Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) işlevine erteler.  
  
- Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.  
  
- `\\.\` ve, mscorlib. dll ' deki dosya g/ç API 'Leri için `\\?\`dahil olmak üzere tam güvende cihaz yolu sözdizimi desteği.  
  
- Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.  
  
- Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.  
  
## <a name="impact"></a>Etki  

.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar için bu değişiklikler varsayılan olarak açık. Daha önce erişilemeyen yollara erişme yöntemlerine izin verirken performansı artırmalıdır.  
  
.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.  
  
## <a name="mitigation"></a>Azaltma  
 .NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve uygulama yapılandırma dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdakileri ekleyerek eski normalleştirmeyi kullanabilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, uygulama. yapılandırma dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
