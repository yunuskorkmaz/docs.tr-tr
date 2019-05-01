---
ms.openlocfilehash: e39b4e85b47902babac7a22a93aa64c2f86ef01f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640074"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData, verileri artık UTF-8 alır.

|   |   |
|---|---|
|Ayrıntılar|Hedef .NET Framework 4 veya .NET Framework 4.5.1 veya önceki sürümlerinde çalışan uygulamalar için <code>DataObject.GetData</code> HTML olarak biçimlendirilmiş verileri bir ASCII dizesi olarak alır. Sonuç olarak, ASCII olmayan karakterler (karakter, ASCII kodları 0x7F büyük olan) iki rastgele karakterler tarafından temsil edilir.<p/>.NET Framework 4.5 veya üzeri ve .NET Framework 4.5.2, çalışma hedefleyen uygulamalar için <code>DataObject.GetData</code> UTF-0x7F büyük karakterler doğru şekilde temsil eden 8 HTML biçimli verileri alır.|
|Öneri|HTML biçimli dizeler kodlama sorun için geçici bir çözüm uygulanan varsa (örneğin, bir HTML dizesi açıkça kodlayarak alınan panodan aktararak <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) ve uygulamanız için 4 4.5 sürümünden yeniden hedefleme, geçici çözüm kaldırılması gerekir. Eski davranışı herhangi bir nedenden dolayı gerekirse, uygulama bu davranışı sağlamak için .NET Framework 4.0 hedefleyebilirsiniz.|
|Kapsam|Kenar|
|Sürüm|4.5.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
