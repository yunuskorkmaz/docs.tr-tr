---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181782"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor

.NET Framework 4.6.1 ' de tanıtılan Uyumlulukanahtarı.NETCore3,0'deWindowsFormsdesteklenmez.`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ile `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` başlayarak, uyumluluk anahtarı <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir uygulamayla <xref:System.IndexOutOfRangeException> çağrıldığında olası özel durumları ele alınmaktadır. Daha fazla bilgi için bkz [. azaltma: Özel IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

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

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
