---
ms.openlocfilehash: a806107456a65a4919592da9535a2617f677cfe0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496681"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="4e651-101">WPF DispatcherSynchronizationContext. CreateCopy şimdi geçerli örnek yerine yeni bir kopya döndürüyor</span><span class="sxs-lookup"><span data-stu-id="4e651-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="4e651-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4e651-102">Details</span></span>

<span data-ttu-id="4e651-103">.NET Framework 4 ' te, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> birincil olarak bir performans iyileştirmesi olarak geçerli örneğe bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e651-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="4e651-104">.NET Framework 4,5 ' de, ilk kez bu eşit başvuruları sonuçlandırma, yürütülen iş parçacığının doğru eşitleme bağlamında olduğunu belirten yeni bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e651-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="4e651-105">Bu başvuruların kimliğini denetleyen kodun etkileneceği, ancak değişiklik nedeniyle çağıran kod, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> .NET Framework 4,5 veya daha yeni bir sürüme geçişin bir parçası olarak test edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4e651-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4e651-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="4e651-106">Suggestion</span></span>

<span data-ttu-id="4e651-107"><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy>Şimdi yeni bir nesne döndüren farkında olun <xref:System.Threading.SynchronizationContext?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="4e651-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="4e651-108">Daha önce, bu şekilde oluşturulan başvuruların denklik olarak kullanıldığı kod gerçekten doğru bağlamda olup olmadığını denetmıyordu, ancak .NET Framework 4,5 veya üzeri bir sürümde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="4e651-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="4e651-109">Soruna neden olma olasılığı düşüktür, etkilenen kod yollarının kullanılması bunun herhangi bir sorun olup olmadığını belirlemede yeterli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e651-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="4e651-110">Name</span><span class="sxs-lookup"><span data-stu-id="4e651-110">Name</span></span>    | <span data-ttu-id="4e651-111">Değer</span><span class="sxs-lookup"><span data-stu-id="4e651-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4e651-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4e651-112">Scope</span></span>   |<span data-ttu-id="4e651-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="4e651-113">Minor</span></span>|
|<span data-ttu-id="4e651-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4e651-114">Version</span></span>|<span data-ttu-id="4e651-115">4,5</span><span class="sxs-lookup"><span data-stu-id="4e651-115">4.5</span></span>|
|<span data-ttu-id="4e651-116">Tür</span><span class="sxs-lookup"><span data-stu-id="4e651-116">Type</span></span>|<span data-ttu-id="4e651-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4e651-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4e651-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4e651-118">Affected APIs</span></span>

- <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy`

-->
