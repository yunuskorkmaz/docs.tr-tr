---
ms.openlocfilehash: 8e37007318a55188d44607fd5e4c4f3950c105df
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761161"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage IMessageFilter.PreFilterMessage a uygulamaları için artık oluşturur.

|   |   |
|---|---|
|Ayrıntılar|Önceki .NET Framework 4.6.1, arama <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> ile bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> olarak adlandırılan <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> veya <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (Ayrıca çağırma sırasında <xref:System.Windows.Forms.Application.DoEvents>) neden olduğu bir <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>.NET Framework 4.6.1'i hedefleyen uygulamalar ile başlayarak, bu artık özel durum ve içe filtreleri yukarıda açıklandığı gibi kullanılabilir.|
|Öneri|Unutmayın, <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> artık a oluşturmaz <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> yukarıda açıklanan davranışı. Bunu kullanarak yalnızca .NET Framework 4.6.1 dışında bu değişikliği özelliğini 4.6.1.Apps .NET Framework hedefleme (veya hedefleme eski çerçeveleri kabul etme uygulamaları) hedefleyen uygulamaları etkiler [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) Uyumluluk anahtarı.|
|Kapsam|Kenar|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

