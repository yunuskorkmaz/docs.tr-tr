---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643972"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.1 içinde tanıtılan `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.7.1 ile başlayarak, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` uyumluluk anahtarı geliştiricilerin bağımsız <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylemleri geri çevirme yapmasına izin verilir. Anahtar, bağlam metni varsa <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> yoksayıldığı eski davranışı geri yükledi ve geliştirici, <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eyleminden önce denetimde <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemi kullanmak için gereklidir. Daha fazla bilgi için bkz. [\<AppContextSwitchOverrides > öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

.NET Core 'da `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` anahtarı desteklenmez.

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

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
