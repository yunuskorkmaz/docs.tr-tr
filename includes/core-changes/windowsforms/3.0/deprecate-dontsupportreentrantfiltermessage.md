---
ms.openlocfilehash: 55c13aa70a03bcc548ce1d096cca8f40de6cda84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721521"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ile başlayarak, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Uyumluluk anahtarı <xref:System.IndexOutOfRangeException> <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel bir uygulamayla çağrıldığında olası özel durumları ele alınmaktadır <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

.NET Core 'da, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
