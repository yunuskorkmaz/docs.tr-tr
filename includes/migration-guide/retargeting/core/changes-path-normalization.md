---
ms.openlocfilehash: 7c4b9faf25853c1c7a546f06c329f6f153eef904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606938"
---
### <a name="changes-in-path-normalization"></a>Yol normalleştirmede değişiklikler

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, çalışma zamanının yol normalleştirme yöntemi değişti. Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir. Normalleştirme genellikle şunları içerir:

- Standart hale getirme bileşeni ve Dizin ayırıcıları.
- Geçerli dizin göreli bir yola uygulanıyor.
- Göreli dizin (.) veya üst dizin (..) bir yolda değerlendiriliyor.
- Belirtilen karakterler kırpılırken.
.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirmede aşağıdaki değişiklikler varsayılan olarak etkindir:
  - Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) işlevine erteler.
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
