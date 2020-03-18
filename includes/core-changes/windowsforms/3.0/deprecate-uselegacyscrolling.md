---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937036"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>DomainUpDown.UseLegacyScrolling uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.1'de tanıtılan `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.7.1 ile `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` başlayan uyumluluk anahtarı, geliştiricilerin bağımsız <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve eylemleri devre dışı bırakmalarına olanak sağladı. Anahtar, bağlam metni varsa göz <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ardı edildiği ve geliştiricinin <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylemden önce denetimüzerinde eylem kullanması gereken eski davranışı geri yükledi. Daha fazla bilgi için [ \<AppContextSwitchOverrides> öğesine](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)bakın.

.NET Core'da `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

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
