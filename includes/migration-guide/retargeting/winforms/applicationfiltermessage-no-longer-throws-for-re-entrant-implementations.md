---
ms.openlocfilehash: 9b184f54650d2efb31ec66f443198b19ceaeb5f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614703"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application. FilterMessage artık IMessageFilter. PreFilterMessage uygulamasının re-entrant uygulamaları için değildir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 önce, <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> çağrılan <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> veya <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> (aynı zamanda çağrılırken) ile çağırma <xref:System.Windows.Forms.Application.DoEvents> bir öğesine neden olur <xref:System.IndexOutOfRangeException?displayProperty=fullName> .<p/>.NET Framework 4.6.1 hedefleyen uygulamalarla başlayarak, bu özel durum artık oluşturulmaz ve yukarıda açıklandığı gibi yeniden entrant filtreleri kullanılabilir.

#### <a name="suggestion"></a>Öneri

<xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)>Yukarıda açıklanan re-entrant davranışı için artık oluşturmadığının farkında olun <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> . Bu yalnızca .NET Framework 4.6.1 hedefleyen uygulamaları etkiler. .NET Framework 4.6.1 hedefleyen uygulamalar, [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) uyumluluk anahtarı kullanılarak bu değişikliği (veya eski çerçeveleri hedefleyen uygulamaları kabul edebilir) devre dışı bırakabilir.

| Name          | Değer       |
|:--------------|:------------|
| Kapsam         | Edge        |
| Sürüm       | 4.6.1       |
| Tür          | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType>
