---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644007"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor

.NET Framework 4.6.1 içinde tanıtılan `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ile başlayarak, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulamasıyla çağrıldığında olası <xref:System.IndexOutOfRangeException> özel durumları ele alınmaktadır. Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

.NET Core 'da `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtarı desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
