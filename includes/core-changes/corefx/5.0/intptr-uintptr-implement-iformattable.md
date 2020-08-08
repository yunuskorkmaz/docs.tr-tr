---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024711"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr ve UIntPtr IFormattable 'ı uygular

<xref:System.IntPtr>ve <xref:System.UIntPtr> Şimdi uygulamasını uygulayın <xref:System.IFormattable> . Desteği denetleyen işlevler <xref:System.IFormattable> artık bu türler için farklı sonuçlar döndürebilir, çünkü bir biçim belirticisi ve bir kültür de geçirebilir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET ' in önceki sürümlerinde <xref:System.IntPtr> ve <xref:System.UIntPtr> uygulamaz <xref:System.IFormattable> . İçin onay veren işlevler <xref:System.IFormattable> , yalnızca veya çağırmak için geri <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> dönebilir <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> , yani biçim belirticileri ve kültürler dikkate alınmıyor.

.NET 5,0 ve sonraki sürümlerde <xref:System.IntPtr> ve <xref:System.UIntPtr> uygulayın <xref:System.IFormattable> . Desteği denetleyen işlevler <xref:System.IFormattable> artık bu türler için farklı sonuçlar döndürebilir, çünkü bir biçim belirticisi ve bir kültür de geçirebilir.

Bu değişiklik, enterpolasyonlu dizeler ve <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> diğerleri arasında senaryolar etkiler.

#### <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.IntPtr>ve <xref:System.UIntPtr> artık C# ' de `nint` ve anahtar kelimeleri aracılığıyla dil desteğine sahiptir `nuint` . Yedekleme türleri, gibi diğer temel türler tarafından sunulan işlevlerle neredeyse eşlik (mümkün olduğunda) sağlayacak şekilde güncelleştirildi <xref:System.Int32?displayProperty=nameWithType> .

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

#### <a name="recommended-action"></a>Önerilen eylem

Bu türlerin değerlerini görüntülerken Biçim belirleyicisi veya özel kültürün kullanılmasını istemiyorsanız, ' <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> nin ve aşırı yüklerini çağırabilirsiniz `ToString()` .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
