---
ms.openlocfilehash: b4b49b55cda26ac9d9760f93e9758aab940ad135
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117222"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="9b857-101">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="9b857-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="9b857-102">Özel <xref:System.Text.EncoderFallbackBuffer> örnekler yinelemeli olarak geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="9b857-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="9b857-103">Uygulamasının uygulanması <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> , hedef kodlamaya dönüştürülebilir bir karakter sırası ile sonuçlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b857-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="9b857-104">Aksi takdirde, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="9b857-104">Otherwise, an exception occurs.</span></span> 

#### <a name="details"></a><span data-ttu-id="9b857-105">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9b857-105">Details</span></span>

<span data-ttu-id="9b857-106">Bir karakterden bayta dönüştürme işlemi sırasında, çalışma zamanı hatalı biçimlendirilmiş veya dönüştürülebilir UTF-16 dizileri algılar ve bu karakterleri <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemine sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b857-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b857-107">Yöntemi, orijinal olmayan veriler için hangi karakterlerin yerine geçmeli olduğunu belirler ve bu karakterler bir döngüde çağırarak <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> boşaltılır. `Fallback`</span><span class="sxs-lookup"><span data-stu-id="9b857-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="9b857-108">Çalışma zamanı daha sonra bu değiştirme karakterlerini hedef kodlamaya dönüştürme girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9b857-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="9b857-109">Bu işlem başarılı olursa, çalışma zamanı özgün giriş dizesinde bıraktığınız yerden kodlamaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="9b857-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span> 

<span data-ttu-id="9b857-110">.NET Core Preview 7 ve önceki sürümlerinde, özel uygulamaları <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir olmayan karakter dizileri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9b857-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="9b857-111">Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, çalışma zamanı <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi değiştirme karakterleriyle bir kez çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yöntemin yeni bir değiştirme sırası döndürmesini bekliyor.</span><span class="sxs-lookup"><span data-stu-id="9b857-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="9b857-112">Bu işlem, çalışma zamanı sonunda iyi biçimlendirilmiş, dönüştürülebilir bir değiştirme veya en fazla özyineleme sayısına ulaşılana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="9b857-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="9b857-113">.NET Core 3,0 ile başlayarak, özel uygulamalarının <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülebilir karakter dizilerini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b857-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="9b857-114">Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9b857-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="9b857-115">Çalışma zamanı artık <xref:System.Text.EncoderFallbackBuffer> örneğe özyinelemeli çağrılar yapmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9b857-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span> 

<span data-ttu-id="9b857-116">Bu davranış yalnızca aşağıdaki koşulların üçü de karşılandığında geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="9b857-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="9b857-117">Çalışma zamanı, hatalı biçimlendirilmiş bir UTF-16 sırası veya hedef kodlamaya dönüştürülemeyen bir UTF-16 sırası algılar.</span><span class="sxs-lookup"><span data-stu-id="9b857-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="9b857-118">Özel <xref:System.Text.EncoderFallback> bir belirtildi.</span><span class="sxs-lookup"><span data-stu-id="9b857-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="9b857-119">Özel <xref:System.Text.EncoderFallback> bir hatalı oluşturulmuş veya dönüştürülebilir UTF-16 sırasını değiştirme girişimleri.</span><span class="sxs-lookup"><span data-stu-id="9b857-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9b857-120">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9b857-120">Version introduced</span></span>

<span data-ttu-id="9b857-121">3.0</span><span class="sxs-lookup"><span data-stu-id="9b857-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b857-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9b857-122">Recommended action</span></span>

<span data-ttu-id="9b857-123">Çoğu geliştirici herhangi bir işlem yapması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9b857-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="9b857-124">Bir uygulama özel <xref:System.Text.EncoderFallback> bir ve <xref:System.Text.EncoderFallbackBuffer> sınıfı kullanıyorsa <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> , uygulama, geri dönüş arabelleğini, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> yöntemi olduğunda hedef kodlamaya doğrudan dönüştürülebilir UTF-16 verileriyle doldurur. İlk olarak çalışma zamanı tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9b857-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="9b857-125">Kategori</span><span class="sxs-lookup"><span data-stu-id="9b857-125">Category</span></span>

<span data-ttu-id="9b857-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="9b857-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b857-127">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9b857-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->