---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620705"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="0d678-101">WPF DispatcherSynchronizationContext. CreateCopy şimdi geçerli örnek yerine yeni bir kopya döndürüyor</span><span class="sxs-lookup"><span data-stu-id="0d678-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="0d678-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0d678-102">Details</span></span>

<span data-ttu-id="0d678-103">.NET Framework 4 ' te, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> birincil olarak bir performans iyileştirmesi olarak geçerli örneğe bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d678-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="0d678-104">.NET Framework 4,5 ' de, ilk kez bu eşit başvuruları sonuçlandırma, yürütülen iş parçacığının doğru eşitleme bağlamında olduğunu belirten yeni bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d678-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="0d678-105">Bu başvuruların kimliğini denetleyen kodun etkileneceği, ancak değişiklik nedeniyle çağıran kod, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> .NET Framework 4,5 veya daha yeni bir sürüme geçişin bir parçası olarak test edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0d678-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0d678-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="0d678-106">Suggestion</span></span>

<span data-ttu-id="0d678-107"><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy>Şimdi yeni bir nesne döndüren farkında olun <xref:System.Threading.SynchronizationContext?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="0d678-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="0d678-108">Daha önce, bu şekilde oluşturulan başvuruların denklik olarak kullanıldığı kod gerçekten doğru bağlamda olup olmadığını denetmıyordu, ancak .NET Framework 4,5 veya üzeri bir sürümde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="0d678-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="0d678-109">Soruna neden olma olasılığı düşüktür, etkilenen kod yollarının kullanılması bunun herhangi bir sorun olup olmadığını belirlemede yeterli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d678-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="0d678-110">Name</span><span class="sxs-lookup"><span data-stu-id="0d678-110">Name</span></span>    | <span data-ttu-id="0d678-111">Değer</span><span class="sxs-lookup"><span data-stu-id="0d678-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0d678-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0d678-112">Scope</span></span>   |<span data-ttu-id="0d678-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="0d678-113">Minor</span></span>|
|<span data-ttu-id="0d678-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0d678-114">Version</span></span>|<span data-ttu-id="0d678-115">4,5</span><span class="sxs-lookup"><span data-stu-id="0d678-115">4.5</span></span>|
|<span data-ttu-id="0d678-116">Tür</span><span class="sxs-lookup"><span data-stu-id="0d678-116">Type</span></span>|<span data-ttu-id="0d678-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="0d678-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0d678-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0d678-118">Affected APIs</span></span>

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
