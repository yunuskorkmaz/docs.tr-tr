---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721523"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException başka bir derlemeye taşındı

<xref:System.ComponentModel.InvalidAsynchronousStateException>Sınıf taşınmış.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.

.NET Core 3,0 ile başlayarak, *System. ComponentModel. ilkel* derleme derlemesinde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, <xref:System.ComponentModel.InvalidAsynchronousStateException> gibi bir yöntemi çağırarak <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ya da türün belirli bir derlemede olduğunu varsayan bir aşırı yüklemesi çağırarak yüklemesi için yansıma kullanan uygulamaları etkiler <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> . Bu durumda, yöntem çağrısında başvurulan derlemeyi, türün yeni derleme konumunu yansıtacak şekilde güncelleştirin.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

#### Affected APIs

- Not detectable via API analysis

-->
