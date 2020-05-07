---
ms.openlocfilehash: 6c35174be50ffc5031d0c4183bd936b4ef27757e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859820"
---
### <a name="sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs"></a>SSE ve SSE2 CompareGreaterThan yöntemleri NaN girdilerini doğru bir şekilde işler

Aşağıdaki <xref:System.Runtime.Intrinsics.X86.Sse?displayProperty=nameWithType> ve <xref:System.Runtime.Intrinsics.X86.Sse2?displayProperty=nameWithType> yöntemleri, girdileri doğru bir şekilde işlemek `NaN` ve <xref:System.Runtime.Intrinsics.X86.Avx?displayProperty=nameWithType> sınıfındaki eşdeğer yöntemlerin donanım davranışıyla eşleştirmek için düzeltildi:

* `CompareGreaterThan`
* `CompareGreaterThanOrEqual`
* `CompareNotGreaterThan`
* `CompareNotGreaterThanOrEqual`
* `CompareScalarGreaterThan`
* `CompareScalarGreaterThanOrEqual`
* `CompareScalarNotGreaterThan`
* `CompareScalarNotGreaterThanOrEqual`

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce `NaN` , listelenmiş <xref:System.Runtime.Intrinsics.X86.Sse> ve <xref:System.Runtime.Intrinsics.X86.Sse2> yöntemlere yapılan girişler yanlış bir sonuç döndürdü. Sonuç, <xref:System.Runtime.Intrinsics.X86.Avx> sınıfında karşılık gelen yöntem tarafından oluşturulan sonuçtan de farklıydı.

.NET 5,0 ' den başlayarak, bu yöntemler girişleri `NaN` doğru şekilde işler ve <xref:System.Runtime.Intrinsics.X86.Avx> sınıftaki karşılık gelen yöntemlerle aynı sonuçları döndürür.

Streaming SIMD Extensions (SSE) ve Streaming SIMD Extensions 2 (SSE2) endüstri standardı mimarileri (IAS), bu karşılaştırma yöntemleri için doğrudan donanım desteği sağlamamakta ve bu nedenle yazılımda uygulanırlar. Daha önce, Yöntemler hatalı şekilde uygulanmıştır ve girdileri yanlış bir şekilde `NaN` işledi. Yerel bilgisayardan gelen kod için hatalı davranış hataları ortaya çıkarabilir. 256 bitlik bir kod yolu için yöntemler, <xref:System.Runtime.Intrinsics.X86.Avx> sınıftaki eşdeğer yöntemlere farklı sonuçlar da üretebilir.

Yöntemlerin daha önceden nasıl yanlış olduğunu gösteren bir örnek olarak, normal tamsayılar için `CompareNotGreaterThan(x,y)` olarak `CompareLessThanOrEqual(x,y)` öğesini uygulayabilirsiniz. Ancak, girişler `NaN` için bu mantık yanlış sonucu hesaplar. Bunun yerine, `CompareNotLessThan(y,x)` sayılar doğru şekilde karşılaştırılmaktadır *ve* girişler dikkate alır `NaN` .

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

#### <a name="recommended-action"></a>Önerilen eylem

- Önceki davranışın bir hata olması durumunda hiçbir değişiklik yapılması gerekmez.

- Önceki davranış isteniyorsa, ilgili çağrıyı aşağıdaki gibi değiştirerek bu davranışı koruyabilirsiniz:

  * `CompareGreaterThan(x,y)` -> `CompareNotLessThanOrEqual(x,y)`
  * `CompareGreaterThanOrEqual(x,y)` -> `CompareNotLessThan(x,y)`
  * `CompareNotGreaterThan(x,y)` -> `CompareLessThanOrEqual(x,y)`
  * `CompareNotGreaterThanOrEqual(x,y)` -> `CompareLessThan(x,y)`
  * `CompareScalarGreaterThan(x,y)` -> `CompareScalarNotLessThanOrEqual(x,y)`
  * `CompareScalarGreaterThanOrEqual(x,y)` -> `CompareScalarNotLessThan(x,y)`
  * `CompareScalarNotGreaterThan(x,y)` -> `CompareScalarLessThanOrEqual(x,y)`
  * `CompareScalarNotGreaterThanOrEqual(x,y)` -> `CompareScalarLessThan(x,y)`

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>

- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`

- `M:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`

-->
