---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614690"
---
### <a name="changes-in-path-normalization"></a>Yol normalleştirmede değişiklikler

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, çalışma zamanının yol normalleştirme yöntemi değişti. Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir. Normalleştirme genellikle şunları içerir:

- Standart hale getirme bileşeni ve Dizin ayırıcıları.
- Geçerli dizin göreli bir yola uygulanıyor.
- Göreli dizin (.) veya üst dizin (..) bir yolda değerlendiriliyor.
- Belirtilen karakterler kırpılırken.
.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirmede aşağıdaki değişiklikler varsayılan olarak etkindir:
  - Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) işlevine erteler.
- Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.
- `\\.\`mscorlib.dll ' deki dosya g/ç API 'leri için ve dahil olmak üzere tam güvende cihaz yolu söz dizimi desteği `\\?\` .
- Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.
- Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.
Bu değişiklikler, daha önce erişilemeyen yollara erişme yöntemlerinin kullanılmasına izin verirken performansı geliştirir. .NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski normalleştirmeyi kullanabilir:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, `<runtime>` uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |
