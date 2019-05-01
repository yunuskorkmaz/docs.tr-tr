---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757813"
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
