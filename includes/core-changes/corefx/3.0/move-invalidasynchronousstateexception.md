---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021610"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>GeçersizAsynchronousStateException başka bir derlemetaşındı

Sınıf <xref:System.ComponentModel.InvalidAsynchronousStateException> taşındı.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 ve önceki <xref:System.ComponentModel.InvalidAsynchronousStateException> sürümlerinde, sınıf *System.ComponentModel.TypeConverter* derlemesinde bulunur.

.NET Core 3.0 ile başlayarak *System.ComponentModel.Primitives* derlemesinde bulunur.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, tür belirli bir <xref:System.ComponentModel.InvalidAsynchronousStateException> derlemede olduğunu <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> varsayar gibi <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> bir yöntem veya aşırı yük çağırarak yüklemek için yansıma kullanan uygulamaları etkiler. Bu durumda, yöntem çağrısında başvurulan derleme derleme sürünün yeni derleme konumunu yansıtacak şekilde güncelleştirilmelidir.

#### <a name="category"></a>Kategori

Çekirdek .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
