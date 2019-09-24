---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217103"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException başka bir derlemeye taşındı

<xref:System.ComponentModel.InvalidAsynchronousStateException> Sınıf taşınmış.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.

.NET Core 3,0 ile başlayarak, *System. ComponentModel. ilkel* derleme derlemesinde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, <xref:System.ComponentModel.InvalidAsynchronousStateException> gibi <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> bir yöntemi çağırarak ya da türün belirli bir derlemede olduğunu varsayan bir aşırı yüklemesi <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> çağırarak yüklemesi için yansıma kullanan uygulamaları etkiler. Böyle bir durumda, yöntem çağrısında başvurulan derlemenin, türün yeni derleme konumunu yansıtacak şekilde güncellenmesi gerekir.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
