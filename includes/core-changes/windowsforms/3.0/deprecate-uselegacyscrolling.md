---
ms.openlocfilehash: ee4a27dde9f1e7756401e3d8b709514082f5d3b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556243"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.NET Framework 4.7.1 ' de tanıtılan uyumluluk anahtarı .NET Core veya .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.7.1 ile başlayarak, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` Uyumluluk anahtarı geliştiricilerin bağımsız ve eylemleri kabul etmelerine izin verilir <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Anahtar, bağlam metni varsa yoksayılan eski davranışı geri yükledi <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve bu, geliştiricinin eylemden <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> önce denetimde eylemi kullanması gerekir <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [ \<AppContextSwitchOverrides> öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

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
