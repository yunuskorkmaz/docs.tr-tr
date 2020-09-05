---
ms.openlocfilehash: 277a91fbfbf0c6aaaa0dc044ef0c079ad8607699
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497421"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="71198-101">BlockingCollection &lt; T &gt; . TryTakeFromAny artık throw</span><span class="sxs-lookup"><span data-stu-id="71198-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="71198-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71198-102">Details</span></span>

<span data-ttu-id="71198-103">Giriş koleksiyonlarından biri tamamlandı olarak işaretlenmişse, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> artık-1 döndürmez ve <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> artık özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="71198-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="71198-104">Bu değişiklik, koleksiyonlardan biri boş veya tamamlanmış olduğunda koleksiyonlarla çalışmayı mümkün kılar, ancak diğer koleksiyonda hala alınabilecek öğeler bulunur.</span><span class="sxs-lookup"><span data-stu-id="71198-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="71198-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="71198-105">Suggestion</span></span>

<span data-ttu-id="71198-106">Bir engelleme koleksiyonunun tamamlanması durumunda denetim akışı amacıyla TryTakeFromAny döndüren-1 veya TakeFromAny oluşturma kullanılıyorsa, bu kodun artık <code>.Any(b =&gt; b.IsCompleted)</code> Bu koşulu algılaması için kullanılacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="71198-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="71198-107">Name</span><span class="sxs-lookup"><span data-stu-id="71198-107">Name</span></span>    | <span data-ttu-id="71198-108">Değer</span><span class="sxs-lookup"><span data-stu-id="71198-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="71198-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="71198-109">Scope</span></span>   |<span data-ttu-id="71198-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="71198-110">Minor</span></span>|
|<span data-ttu-id="71198-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="71198-111">Version</span></span>|<span data-ttu-id="71198-112">4,5</span><span class="sxs-lookup"><span data-stu-id="71198-112">4.5</span></span>|
|<span data-ttu-id="71198-113">Tür</span><span class="sxs-lookup"><span data-stu-id="71198-113">Type</span></span>|<span data-ttu-id="71198-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="71198-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="71198-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="71198-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Threading.CancellationToken)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Int32)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``

-->
