---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620552"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="1f1ba-101">BlockingCollection &lt; T &gt; . TryTakeFromAny artık throw</span><span class="sxs-lookup"><span data-stu-id="1f1ba-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="1f1ba-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1f1ba-102">Details</span></span>

<span data-ttu-id="1f1ba-103">Giriş koleksiyonlarından biri tamamlandı olarak işaretlenmişse, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> artık-1 döndürmez ve <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> artık özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1f1ba-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="1f1ba-104">Bu değişiklik, koleksiyonlardan biri boş veya tamamlanmış olduğunda koleksiyonlarla çalışmayı mümkün kılar, ancak diğer koleksiyonda hala alınabilecek öğeler bulunur.</span><span class="sxs-lookup"><span data-stu-id="1f1ba-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1f1ba-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="1f1ba-105">Suggestion</span></span>

<span data-ttu-id="1f1ba-106">Bir engelleme koleksiyonunun tamamlanması durumunda denetim akışı amacıyla TryTakeFromAny döndüren-1 veya TakeFromAny oluşturma kullanılıyorsa, bu kodun artık <code>.Any(b =&gt; b.IsCompleted)</code> Bu koşulu algılaması için kullanılacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f1ba-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="1f1ba-107">Name</span><span class="sxs-lookup"><span data-stu-id="1f1ba-107">Name</span></span>    | <span data-ttu-id="1f1ba-108">Değer</span><span class="sxs-lookup"><span data-stu-id="1f1ba-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1f1ba-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1f1ba-109">Scope</span></span>   |<span data-ttu-id="1f1ba-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="1f1ba-110">Minor</span></span>|
|<span data-ttu-id="1f1ba-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1f1ba-111">Version</span></span>|<span data-ttu-id="1f1ba-112">4,5</span><span class="sxs-lookup"><span data-stu-id="1f1ba-112">4.5</span></span>|
|<span data-ttu-id="1f1ba-113">Tür</span><span class="sxs-lookup"><span data-stu-id="1f1ba-113">Type</span></span>|<span data-ttu-id="1f1ba-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="1f1ba-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f1ba-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1f1ba-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|
