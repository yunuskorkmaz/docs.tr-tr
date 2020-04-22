---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021603"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="53115-101">Özel EncoderFallbackBuffer örnekleri özyinelemeli geri düşemez</span><span class="sxs-lookup"><span data-stu-id="53115-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="53115-102">Özel <xref:System.Text.EncoderFallbackBuffer> örnekler özyinelemeli olarak geri alınamaz.</span><span class="sxs-lookup"><span data-stu-id="53115-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="53115-103">Uygulanması hedef <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> kodlama dönüştürülebilir bir karakter dizisi neden olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53115-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="53115-104">Aksi takdirde, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="53115-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="53115-105">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="53115-105">Change description</span></span>

<span data-ttu-id="53115-106">Karakterden bayta transkodlama işlemi sırasında, çalışma zamanı yanlış biçimlendirilmiş veya dönüştürülemeyen UTF-16 dizilerini algılar <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ve bu karakterleri yönteme sağlar.</span><span class="sxs-lookup"><span data-stu-id="53115-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="53115-107">Yöntem, `Fallback` hangi karakterlerin özgün dönüştürülemez verilerle değiştirilmesi gerektiğini belirler ve bu karakterler bir <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> döngü içinde çağrılarak boşaltılır.</span><span class="sxs-lookup"><span data-stu-id="53115-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="53115-108">Çalışma süresi daha sonra bu ikame karakterleri hedef kodlamaya aktarmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="53115-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="53115-109">Bu işlem başarılı olursa, çalışma süresi özgün giriş dizesinde kaldığı yerden kodlamaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="53115-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="53115-110">.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> hedef kodlamaya dönüştürülemeyen karakter dizilerini özel uygulamalar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="53115-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="53115-111">Değiştirilen karakterler hedef kodlamaya aktarılamıyorsa, çalışma zamanı <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi değiştirme karakterleri ile bir kez daha çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yöntemin yeni bir değiştirme sırası döndürmesini bekleyiş eder.</span><span class="sxs-lookup"><span data-stu-id="53115-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="53115-112">Bu işlem, çalışma süresi sonunda iyi biçimlendirilmiş, dönüştürülebilir bir ikame görene veya maksimum özyineleme sayısına ulaşılAna kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="53115-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="53115-113">.NET Core 3.0 ile başlayarak, hedef kodlamaya dönüştürülebilen karakter dizilerini özel uygulamaları <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="53115-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="53115-114">Değiştirilen karakterler hedef kodlamaya çevrilemiyorsa, bir <xref:System.ArgumentException> atılmıştır.</span><span class="sxs-lookup"><span data-stu-id="53115-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="53115-115">Çalışma süresi artık <xref:System.Text.EncoderFallbackBuffer> örneğine özyinelemeli çağrılar yapmaz.</span><span class="sxs-lookup"><span data-stu-id="53115-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="53115-116">Bu davranış yalnızca aşağıdaki koşulların üçü karşılandığında geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="53115-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="53115-117">Çalışma zamanı, hedef kodlamaya dönüştürülemeyen kötü biçimlendirilmiş bir UTF-16 dizisi veya UTF-16 dizisi algılar.</span><span class="sxs-lookup"><span data-stu-id="53115-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="53115-118">Bir <xref:System.Text.EncoderFallback> özel belirtildi.</span><span class="sxs-lookup"><span data-stu-id="53115-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="53115-119">Özel <xref:System.Text.EncoderFallback> girişimleri yeni bir kötü biçimli veya dönüştürülemez UTF-16 dizisi yerine.</span><span class="sxs-lookup"><span data-stu-id="53115-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="53115-120">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="53115-120">Version introduced</span></span>

<span data-ttu-id="53115-121">3,0</span><span class="sxs-lookup"><span data-stu-id="53115-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="53115-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="53115-122">Recommended action</span></span>

<span data-ttu-id="53115-123">Çoğu geliştiricinin herhangi bir işlem yapmanıza gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="53115-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="53115-124">Bir <xref:System.Text.EncoderFallback> uygulama özel ve <xref:System.Text.EncoderFallbackBuffer> sınıf kullanıyorsa, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> yöntem ilk çalıştırma zamanı tarafından çağrıldığınızda doğrudan hedef kodlamadönüştürülebilir iyi biçimlendirilmiş UTF-16 verileri ile geri dönüş arabelleği doldurulur uygulanması nı sağlamak.</span><span class="sxs-lookup"><span data-stu-id="53115-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="53115-125">Kategori</span><span class="sxs-lookup"><span data-stu-id="53115-125">Category</span></span>

<span data-ttu-id="53115-126">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="53115-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="53115-127">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="53115-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
