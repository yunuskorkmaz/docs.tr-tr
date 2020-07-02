---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614631"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>URI 'Lerinde Unicode çift yönlü denetim karakterlerine izin ver

#### <a name="details"></a>Ayrıntılar

Unicode, metnin yönünü belirtmek için kullanılan birkaç özel denetim karakterini belirtir. .NET Framework önceki sürümlerinde bu karakterler, yüzde olarak kodlanmış biçiminde olsa bile tüm URI 'lerden yanlış şekilde kaldırıldı. [RFC 3987](https://tools.ietf.org/html/rfc3987)' i daha iyi izlemek Için artık URI 'lerinde Bu karakterlere izin veririz. URI 'de kodlanmamış olarak bulunursa, yüzde olarak kodlanır. Yüzde kodlamalı olduğunda, her zaman olduğu gibi kalır.

#### <a name="suggestion"></a>Öneri

4.7.2 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için, Unicode çift yönlü karakterler için destek varsayılan olarak etkindir. Bu değişiklik istenmeyen ise, [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContextSwitchOverrides anahtarını ekleyerek devre dışı bırakabilirsiniz:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

.NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 ile başlayan sürümler altında çalışan uygulamalar için, Unicode çift yönlü karakterler için destek varsayılan olarak devre dışıdır. Aşağıdaki [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarını `<runtime>` uygulama yapılandırma dosyasının bölümüne ekleyerek etkinleştirebilirsiniz::

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri?displayProperty=nameWithType>
