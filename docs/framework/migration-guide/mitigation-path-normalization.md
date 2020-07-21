---
title: 'Risk azaltma: yol normalleştirme'
description: .NET Framework 'teki yol normalleştirmesini .NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 89dcc46d9f266ffd3635dc0cc02b634720356eda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475222"
---
# <a name="mitigation-path-normalization"></a>Risk azaltma: yol normalleştirme
.NET Framework 4.6.2 hedeflenen uygulamalarla başlayarak .NET Framework yol normalleştirme değişmiştir.  
  
## <a name="what-is-path-normalization"></a>Yol normalleştirme nedir?  
 Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir. Normalleştirme genellikle şunları içerir:  
  
- Standart hale getirme bileşeni ve Dizin ayırıcıları.  
  
- Geçerli dizin göreli bir yola uygulanıyor.  
  
- Bir yoldaki göreli dizin ( `.` ) veya üst dizin ( `..` ) değerlendiriliyor.  
  
- Belirtilen karakterler kırpılırken.  
  
## <a name="the-changes"></a>Değişiklikler  
 .NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirme aşağıdaki yollarla değiştirilmiştir:  
  
- Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) işlevine erteler.  
  
- Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.  
  
- `\\.\`mscorlib.dll ' deki dosya g/ç API 'leri için ve dahil olmak üzere tam güvende cihaz yolu söz dizimi desteği `\\?\` .  
  
- Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.  
  
- Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.  
  
## <a name="impact"></a>Etki  

.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar için bu değişiklikler varsayılan olarak açık. Daha önce erişilemeyen yollara erişme yöntemlerine izin verirken performansı artırmalıdır.  
  
.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.  
  
## <a name="mitigation"></a>Risk azaltma  
 .NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski normalleştirmeyi kullanabilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
