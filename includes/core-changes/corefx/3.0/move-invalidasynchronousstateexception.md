---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568172"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException başka bir derlemeye taşındı

<xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı taşındı.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde <xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.

.NET Core 3,0 ile başlayarak, *System. ComponentModel. ilkel* derleme derlemesinde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya türün belirli bir derlemede olduğunu varsayan bir <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> aşırı yüklemesi çağırarak <xref:System.ComponentModel.InvalidAsynchronousStateException> yüklemek için yansıma kullanan uygulamaları etkiler. Böyle bir durumda, yöntem çağrısında başvurulan derlemenin, türün yeni derleme konumunu yansıtacak şekilde güncellenmesi gerekir.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
