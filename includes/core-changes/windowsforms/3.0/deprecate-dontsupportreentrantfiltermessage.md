---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937011"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor

.NET Framework 4.6.1'de tanıtılan `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.6.1'den `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` başlayarak, <xref:System.IndexOutOfRangeException> <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir uygulamayla çağrıldığında uyumluluk anahtarı olası özel durumları giderer. Daha fazla bilgi için [bkz: Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları.](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)

.NET Core'da `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
