---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614666"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>System. Uri ' nin tutarlı bir ayrılmış karakter kümesi kullandığından emin olun

#### <a name="details"></a>Ayrıntılar

<xref:System.Uri?displayProperty=fullName>' De, bazen kodu çözülmüş bazı yüzde kodlamalı karakterler artık sürekli olarak ayrıldı. Bu, URI 'nin yoluna, sorguya, parçaya veya UserInfo bileşenlerine erişen Özellikler ve Yöntemler genelinde oluşur. Davranış yalnızca aşağıdakilerin her ikisi de doğru olduğunda değişir:

- URI, aşağıdaki ayrılmış karakterlerden herhangi birinin kodlanmış biçimini içerir: `:` , `'` ,, `(` `)` `!` veya `*` .
- URI, Unicode veya kodlanmış ayrılmamış bir karakter içeriyor. Yukarıdakilerin her ikisi de doğruysa, kodlanan ayrılmış karakterler bırakılır. .NET Framework önceki sürümlerinde, bunların kodu çözülür.

#### <a name="suggestion"></a>Öneri

4.7.2 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için yeni kod çözme davranışı varsayılan olarak etkindir. Bu değişiklik istenmeyen ise, [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContextSwitchOverrides anahtarını ekleyerek devre dışı bırakabilirsiniz:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

.NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 ile başlayan sürümler altında çalışan uygulamalar için yeni kod çözme davranışı varsayılan olarak devre dışıdır. Aşağıdaki [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarını `<runtime>` uygulama yapılandırma dosyasının bölümüne ekleyerek etkinleştirebilirsiniz:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri?displayProperty=nameWithType>
