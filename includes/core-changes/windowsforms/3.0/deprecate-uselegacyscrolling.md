---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721031"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.NET Framework 4.7.1 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.7.1 ile başlayarak, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` Uyumluluk anahtarı geliştiricilerin bağımsız ve eylemleri kabul etmelerine izin verilir <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Anahtar, bağlam metni varsa yoksayılan eski davranışı geri yükledi <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve bu, geliştiricinin eylemden <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> önce denetimde eylemi kullanması gerekir <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [ \< AppContextSwitchOverrides> öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

.NET Core 'da, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
