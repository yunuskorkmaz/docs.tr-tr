---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568124"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Özel EncoderFallbackBuffer örnekleri özyinelemeli geri düşemez

Özel <xref:System.Text.EncoderFallbackBuffer> örnekler özyinelemeli olarak geri alınamaz. Uygulanması hedef <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> kodlama dönüştürülebilir bir karakter dizisi neden olmalıdır. Aksi takdirde, bir özel durum oluşur.

#### <a name="change-description"></a>Açıklamayı değiştir

Karakterden bayta transkodlama işlemi sırasında, çalışma zamanı yanlış biçimlendirilmiş veya dönüştürülemeyen UTF-16 dizilerini algılar <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ve bu karakterleri yönteme sağlar. Yöntem, `Fallback` hangi karakterlerin özgün dönüştürülemez verilerle değiştirilmesi gerektiğini belirler ve bu karakterler bir <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> döngü içinde çağrılarak boşaltılır.

Çalışma süresi daha sonra bu ikame karakterleri hedef kodlamaya aktarmaya çalışır. Bu işlem başarılı olursa, çalışma süresi özgün giriş dizesinde kaldığı yerden kodlamaya devam eder.

.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülemeyen karakter dizilerini özel uygulamalar döndürebilir. Değiştirilen karakterler hedef kodlamaya aktarılamıyorsa, çalışma zamanı <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi değiştirme karakterleri ile bir kez daha çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yöntemin yeni bir değiştirme sırası döndürmesini bekleyiş eder. Bu işlem, çalışma süresi sonunda iyi biçimlendirilmiş, dönüştürülebilir bir ikame görene veya maksimum özyineleme sayısına ulaşılAna kadar devam eder.

.NET Core 3.0 ile başlayarak, hedef kodlamaya dönüştürülebilen karakter dizilerini özel uygulamaları <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> döndürmelidir. Değiştirilen karakterler hedef kodlamaya çevrilemiyorsa, bir <xref:System.ArgumentException> atılmıştır. Çalışma süresi artık <xref:System.Text.EncoderFallbackBuffer> örneğine özyinelemeli çağrılar yapmaz.

Bu davranış yalnızca aşağıdaki koşulların üçü karşılandığında geçerlidir:

- Çalışma zamanı, hedef kodlamaya dönüştürülemeyen kötü biçimlendirilmiş bir UTF-16 dizisi veya UTF-16 dizisi algılar.
- Bir <xref:System.Text.EncoderFallback> özel belirtildi.
- Özel <xref:System.Text.EncoderFallback> girişimleri yeni bir kötü biçimli veya dönüştürülemez UTF-16 dizisi yerine.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu geliştiricinin herhangi bir işlem yapmanıza gerek yoktur.

Bir <xref:System.Text.EncoderFallback> uygulama özel ve <xref:System.Text.EncoderFallbackBuffer> sınıf kullanıyorsa, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> yöntem ilk çalıştırma zamanı tarafından çağrıldığınızda doğrudan hedef kodlamadönüştürülebilir iyi biçimlendirilmiş UTF-16 verileri ile geri dönüş arabelleği doldurulur uygulanması nı sağlamak.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
