---
ms.openlocfilehash: 00c32c10f77995284264e795d386f699082dcb84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721313"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez

Özel <xref:System.Text.EncoderFallbackBuffer> örnekler yinelemeli olarak geri dönemez. Uygulamasının uygulanması, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir bir karakter sırası ile sonuçlanmalıdır. Aksi takdirde, bir özel durum oluşur.

#### <a name="change-description"></a>Açıklamayı Değiştir

Bir karakterden bayta dönüştürme işlemi sırasında, çalışma zamanı hatalı biçimlendirilmiş veya dönüştürülebilir UTF-16 dizileri algılar ve bu karakterleri <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemine sağlar. `Fallback`Yöntemi, orijinal olmayan veriler için hangi karakterlerin yerine geçmeli olduğunu belirler ve bu karakterler bir döngüde çağırarak boşaltılır <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> .

Çalışma zamanı daha sonra bu değiştirme karakterlerini hedef kodlamaya dönüştürme girişiminde bulunur. Bu işlem başarılı olursa, çalışma zamanı özgün giriş dizesinde bıraktığınız yerden kodlamaya devam eder.

.NET Core Preview 7 ve önceki sürümlerinde, özel uygulamaları <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir olmayan karakter dizileri döndürebilir. Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, çalışma zamanı <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi değiştirme karakterleriyle bir kez çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yöntemin yeni bir değiştirme sırası döndürmesini bekliyor. Bu işlem, çalışma zamanı sonunda iyi biçimlendirilmiş, dönüştürülebilir bir değiştirme veya en fazla özyineleme sayısına ulaşılana kadar devam eder.

.NET Core 3,0 ile başlayarak, özel uygulamalarının <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir karakter dizilerini döndürmesi gerekir. Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, bir oluşturulur <xref:System.ArgumentException> . Çalışma zamanı artık örneğe özyinelemeli çağrılar yapmayacaktır <xref:System.Text.EncoderFallbackBuffer> .

Bu davranış yalnızca aşağıdaki koşulların üçü de karşılandığında geçerlidir:

- Çalışma zamanı, hatalı biçimlendirilmiş bir UTF-16 sırası veya hedef kodlamaya dönüştürülemeyen bir UTF-16 sırası algılar.
- Özel bir <xref:System.Text.EncoderFallback> belirtildi.
- Özel <xref:System.Text.EncoderFallback> bir hatalı oluşturulmuş veya DÖNÜŞTÜRÜLEBILIR UTF-16 sırasını değiştirme girişimleri.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu geliştirici herhangi bir işlem yapması gerekli değildir.

Bir uygulama özel bir <xref:System.Text.EncoderFallback> ve sınıfı kullanıyorsa <xref:System.Text.EncoderFallbackBuffer> , uygulama <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> çalışma zamanı tarafından ilk kez çağrıldığında, uygulamanın, geri dönüş arabelleğini, hedef kodlamaya doğrudan dönüştürülebilir UTF-16 verileriyle doldurmasıdır.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
