---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556244"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core ve .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ile başlayarak, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Uyumluluk anahtarı <xref:System.IndexOutOfRangeException> <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel bir uygulamayla çağrıldığında olası özel durumları ele alınmaktadır <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

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
