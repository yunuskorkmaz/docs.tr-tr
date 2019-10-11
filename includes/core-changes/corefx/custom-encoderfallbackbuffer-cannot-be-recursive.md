---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237483"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="681d5-101">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="681d5-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="681d5-102">Özel <xref:System.Text.EncoderFallbackBuffer> örnekleri yinelemeli olarak geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="681d5-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="681d5-103">@No__t-0 ' nin uygulanması, hedef kodlamaya dönüştürülebilir bir karakter sırası ile sonuçlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="681d5-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="681d5-104">Aksi takdirde, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="681d5-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="681d5-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="681d5-105">Change description</span></span>

<span data-ttu-id="681d5-106">Bir karakterden bayta dönüştürme işlemi sırasında, çalışma zamanı hatalı biçimlendirilmiş veya dönüştürülebilir UTF-16 dizileri algılar ve bu karakterleri <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemine sağlar.</span><span class="sxs-lookup"><span data-stu-id="681d5-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="681d5-107">@No__t-0 yöntemi, orijinal olmayan veriler için hangi karakterlerin yerine geçmeli olduğunu belirler ve bu karakterler bir döngüde <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> çağırarak boşaltılır.</span><span class="sxs-lookup"><span data-stu-id="681d5-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="681d5-108">Çalışma zamanı daha sonra bu değiştirme karakterlerini hedef kodlamaya dönüştürme girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="681d5-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="681d5-109">Bu işlem başarılı olursa, çalışma zamanı özgün giriş dizesinde bıraktığınız yerden kodlamaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="681d5-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="681d5-110">.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> ' ın özel uygulamaları, hedef kodlamaya dönüştürülebilir olmayan karakter dizileri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="681d5-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="681d5-111">Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, çalışma zamanı değiştirme karakterleriyle bir kez <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemini çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yönteminin yeni bir değiştirme sırası döndürmesini bekliyor.</span><span class="sxs-lookup"><span data-stu-id="681d5-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="681d5-112">Bu işlem, çalışma zamanı sonunda iyi biçimlendirilmiş, dönüştürülebilir bir değiştirme veya en fazla özyineleme sayısına ulaşılana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="681d5-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="681d5-113">.NET Core 3,0 ile başlayarak, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> ' ın özel uygulamaları hedef kodlamaya dönüştürülebilir karakter dizilerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="681d5-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="681d5-114">Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="681d5-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="681d5-115">Çalışma zamanı artık <xref:System.Text.EncoderFallbackBuffer> örneğine özyinelemeli çağrılar yapmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="681d5-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="681d5-116">Bu davranış yalnızca aşağıdaki koşulların üçü de karşılandığında geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="681d5-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="681d5-117">Çalışma zamanı, hatalı biçimlendirilmiş bir UTF-16 sırası veya hedef kodlamaya dönüştürülemeyen bir UTF-16 sırası algılar.</span><span class="sxs-lookup"><span data-stu-id="681d5-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="681d5-118">Özel bir <xref:System.Text.EncoderFallback> belirtildi.</span><span class="sxs-lookup"><span data-stu-id="681d5-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="681d5-119">Özel <xref:System.Text.EncoderFallback>, yeni bir hatalı oluşturulmuş veya dönüştürülebilir UTF-16 sırasını değiştirme girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="681d5-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="681d5-120">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="681d5-120">Version introduced</span></span>

<span data-ttu-id="681d5-121">3.0</span><span class="sxs-lookup"><span data-stu-id="681d5-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="681d5-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="681d5-122">Recommended action</span></span>

<span data-ttu-id="681d5-123">Çoğu geliştirici herhangi bir işlem yapması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="681d5-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="681d5-124">Bir uygulama özel bir <xref:System.Text.EncoderFallback> ve <xref:System.Text.EncoderFallbackBuffer> sınıfı kullanıyorsa, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> yöntemi ilk kez çağrıldığında <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> uygulamasının, geri dönüş arabelleğini, hedef kodlamaya doğrudan dönüştürülebilir UTF-16 verileriyle doldurmasıdır. çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="681d5-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="681d5-125">Kategori</span><span class="sxs-lookup"><span data-stu-id="681d5-125">Category</span></span>

<span data-ttu-id="681d5-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="681d5-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="681d5-127">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="681d5-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
