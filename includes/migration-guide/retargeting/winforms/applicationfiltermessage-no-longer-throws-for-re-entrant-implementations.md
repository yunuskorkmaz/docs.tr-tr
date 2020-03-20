---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804325"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage artık IMessageFilter.PreFilterMessage'ın yeniden giriş uygulamaları için atmıyor

|   |   |
|---|---|
|Ayrıntılar|Önce .NET Framework 4.6.1, <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> denilen <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> veya <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (aynı zamanda <xref:System.Windows.Forms.Application.DoEvents>arama) <xref:System.IndexOutOfRangeException?displayProperty=name>bir neden olacak bir ile arama .<p/>.NET Framework 4.6.1'i hedefleyen uygulamalardan başlayarak, bu özel durum artık atılmaz ve yukarıda açıklandığı gibi yeniden giren filtreler kullanılabilir.|
|Öneri|Yukarıda açıklanan <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> yeniden giren <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> davranışın artık atmayacağını unutmayın. Bu yalnızca .NET Framework 4.6.1'i hedefleyen .NET Framework 4.6.1'i hedefleyen uygulamaları etkiler ve [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) uyumluluk anahtarını kullanarak bu değişikliği (veya eski Çerçeveleri hedefleyen uygulamalar kabul edebilir).|
|Kapsam|Edge|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
