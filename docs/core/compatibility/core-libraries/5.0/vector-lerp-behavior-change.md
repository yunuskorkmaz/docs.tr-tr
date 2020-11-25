---
title: 'Son değişiklik: Vector2. Lerp ve Vector4. Lerp için davranış değişikliği'
description: Vector2. Lerp ve Vector4. Lerp uygulamasının bir kayan noktalı yuvarlama hatası için doğru hesapta değiştiği, çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 8e363a559dba8b7563c40637c47f101d59951216
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761410"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="e6a9c-103">Vector2. Lerp ve Vector4. Lerp için davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="e6a9c-103">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="e6a9c-104"><xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> Bir kayan nokta yuvarlama hatası için uygulamasının uygulanması ve doğru hesaba değiştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="e6a9c-104">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

## <a name="change-description"></a><span data-ttu-id="e6a9c-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e6a9c-105">Change description</span></span>

<span data-ttu-id="e6a9c-106">Daha önce <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> ve <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> olarak uygulandı `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="e6a9c-106">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="e6a9c-107">Ancak, bir kayan nokta yuvarlama hatası nedeniyle, bu algoritma olduğunda her zaman döndürmez `value2` `amount` `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="e6a9c-107">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="e6a9c-108">.NET 5,0 ve üzeri sürümlerde, uygulama ile aynı algoritmayı kullanır <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="e6a9c-108">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="e6a9c-109">Bu algoritma, yuvarlama hatası için doğru şekilde hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e6a9c-109">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="e6a9c-110">Şimdi, ne zaman, `amount` `1.0f` sonuç kesin olarak olur `value2` .</span><span class="sxs-lookup"><span data-stu-id="e6a9c-110">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="e6a9c-111">Güncelleştirilmiş algoritma Ayrıca algoritmaların kullanılabilir olduğunda, kullanımı uygun şekilde iyileştirilme olanağı sağlar <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6a9c-111">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e6a9c-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e6a9c-112">Version introduced</span></span>

<span data-ttu-id="e6a9c-113">5.0</span><span class="sxs-lookup"><span data-stu-id="e6a9c-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e6a9c-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e6a9c-114">Recommended action</span></span>

<span data-ttu-id="e6a9c-115">Herhangi bir işlem gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e6a9c-115">No action is necessary.</span></span> <span data-ttu-id="e6a9c-116">Ancak, eski davranışı sürdürmek istiyorsanız, `Lerp` önceki algoritmasını kullanan kendi işlevinizi uygulayabilirsiniz `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="e6a9c-116">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e6a9c-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e6a9c-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
