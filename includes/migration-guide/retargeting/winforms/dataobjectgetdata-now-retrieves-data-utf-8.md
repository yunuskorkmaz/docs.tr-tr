---
ms.openlocfilehash: e39b4e85b47902babac7a22a93aa64c2f86ef01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804673"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData artık UTF-8 olarak veri alır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4'e yönelik veya .NET Framework 4.5.1 veya <code>DataObject.GetData</code> önceki sürümlerde çalışan uygulamalar için HTML biçimli verileri ASCII dizesi olarak alır. Sonuç olarak, ASCII olmayan karakterler (ASCII kodları 0x7F'den büyük olan karakterler) iki rasgele karakterle temsil edilir.<p/>.NET Framework 4.5 veya sonraki lerini hedefleyen ve .NET Framework 4.5.2 üzerinde çalışan uygulamalar için HTML <code>DataObject.GetData</code> biçimli verileri UTF-8 olarak alır ve bu da 0x7F'den büyük karakterleri doğru bir şekilde temsil eder.|
|Öneri|HTML biçimli dizeleri ile kodlama sorunu için bir geçici çözüm uyguladıysanız (örneğin, Pano'dan alınan HTML dizesini <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>geçirerek açıkça kodlayarak) ve uygulamanızı sürüm 4'ten 4.5'e kadar yeniden hedefliyorsanız, bu geçici çözüm kaldırılmalıdır. Eski davranış nedense gerekli yse, uygulama bu davranışı almak için .NET Framework 4.0'ı hedefleyebilir.|
|Kapsam|Edge|
|Sürüm|4.5.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
