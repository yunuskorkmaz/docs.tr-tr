---
ms.openlocfilehash: b4b49b55cda26ac9d9760f93e9758aab940ad135
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117222"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez

Özel <xref:System.Text.EncoderFallbackBuffer> örnekler yinelemeli olarak geri dönemez. Uygulamasının uygulanması <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> , hedef kodlamaya dönüştürülebilir bir karakter sırası ile sonuçlanmalıdır. Aksi takdirde, bir özel durum oluşur. 

#### <a name="details"></a>Ayrıntılar

Bir karakterden bayta dönüştürme işlemi sırasında, çalışma zamanı hatalı biçimlendirilmiş veya dönüştürülebilir UTF-16 dizileri algılar ve bu karakterleri <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemine sağlar. Yöntemi, orijinal olmayan veriler için hangi karakterlerin yerine geçmeli olduğunu belirler ve bu karakterler bir döngüde çağırarak <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> boşaltılır. `Fallback`

Çalışma zamanı daha sonra bu değiştirme karakterlerini hedef kodlamaya dönüştürme girişiminde bulunur. Bu işlem başarılı olursa, çalışma zamanı özgün giriş dizesinde bıraktığınız yerden kodlamaya devam eder. 

.NET Core Preview 7 ve önceki sürümlerinde, özel uygulamaları <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir olmayan karakter dizileri döndürebilir. Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, çalışma zamanı <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi değiştirme karakterleriyle bir kez çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yöntemin yeni bir değiştirme sırası döndürmesini bekliyor. Bu işlem, çalışma zamanı sonunda iyi biçimlendirilmiş, dönüştürülebilir bir değiştirme veya en fazla özyineleme sayısına ulaşılana kadar devam eder.

.NET Core 3,0 ile başlayarak, özel uygulamalarının <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir karakter dizilerini döndürmesi gerekir. Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, bir <xref:System.ArgumentException> oluşturulur. Çalışma zamanı artık <xref:System.Text.EncoderFallbackBuffer> örneğe özyinelemeli çağrılar yapmayacaktır. 

Bu davranış yalnızca aşağıdaki koşulların üçü de karşılandığında geçerlidir:

- Çalışma zamanı, hatalı biçimlendirilmiş bir UTF-16 sırası veya hedef kodlamaya dönüştürülemeyen bir UTF-16 sırası algılar.
- Özel <xref:System.Text.EncoderFallback> bir belirtildi.
- Özel <xref:System.Text.EncoderFallback> bir hatalı oluşturulmuş veya dönüştürülebilir UTF-16 sırasını değiştirme girişimleri.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu geliştirici herhangi bir işlem yapması gerekli değildir.

Bir uygulama özel <xref:System.Text.EncoderFallback> bir ve <xref:System.Text.EncoderFallbackBuffer> sınıfı kullanıyorsa <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> , uygulama, geri dönüş arabelleğini, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> yöntemi olduğunda hedef kodlamaya doğrudan dönüştürülebilir UTF-16 verileriyle doldurur. İlk olarak çalışma zamanı tarafından çağırılır.

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