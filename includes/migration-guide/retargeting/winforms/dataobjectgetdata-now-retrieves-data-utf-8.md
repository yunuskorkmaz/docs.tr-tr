---
ms.openlocfilehash: c800b3fcc1eff5d7a669611cb0697aa8c87a37a4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804673"
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

