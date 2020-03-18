---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147555"
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

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
