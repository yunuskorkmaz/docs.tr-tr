---
ms.openlocfilehash: f50022d9a7bacd7be40fe3050ced26e7c25cf7aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496372"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a><span data-ttu-id="7d5b3-101">Özel bir ıNC koleksiyonundan öğe kaldırılırken seçicide kilitlenme</span><span class="sxs-lookup"><span data-stu-id="7d5b3-101">Crash in Selector when removing an item from a custom INCC collection</span></span>

#### <a name="details"></a><span data-ttu-id="7d5b3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7d5b3-102">Details</span></span>

<span data-ttu-id="7d5b3-103"><code>T:System.InvalidOperationException</code>Aşağıdaki senaryoda bir durum oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="7d5b3-103">An <code>T:System.InvalidOperationException</code> can occur in the following scenario:</span></span><ul><li><span data-ttu-id="7d5b3-104">A için ItemSource, <code>T:System.Windows.Controls.Primitives.Selector</code> özel bir uygulamasına sahip bir koleksiyondur <code>T:System.Collections.Specialized.INotifyCollectionChanged</code> .</span><span class="sxs-lookup"><span data-stu-id="7d5b3-104">The ItemsSource for a <code>T:System.Windows.Controls.Primitives.Selector</code> is a collection with a custom implementation of <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span></span></li><li><span data-ttu-id="7d5b3-105">Seçili öğe koleksiyondan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="7d5b3-105">The selected item is removed from the collection.</span></span></li><li><span data-ttu-id="7d5b3-106">, <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> =-1 ' dir (bilinmeyen bir konum olduğunu gösterir).</span><span class="sxs-lookup"><span data-stu-id="7d5b3-106">The <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indicating an unknown position).</span></span></li></ul><span data-ttu-id="7d5b3-107">Özel durumun çağrı yığını, System. Windows. Controls. basitler. Selector. getııselected (DependencyObject öğesi) konumundaki System. Windows. DependencyObject. Dispatcher. doğrulamaları yaccess () konumunda başlar. bu durum, uygulamanın birden fazla Dağıtıcı iş parçacığı varsa .NET Framework 4,5 ' de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7d5b3-107">The exception's callstack begins at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)This exception can occur in .NET Framework 4.5 if the application has more than one Dispatcher thread.</span></span> <span data-ttu-id="7d5b3-108">.NET Framework 4,7 ' de, özel durum tek bir dağıtıcı iş parçacığı olan uygulamalarda da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7d5b3-108">In .NET Framework 4.7 the exception can also occur in applications with a single Dispatcher thread.</span></span> <span data-ttu-id="7d5b3-109">Sorun .NET Framework 4.7.1 içinde düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="7d5b3-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7d5b3-110">Öneri</span><span class="sxs-lookup"><span data-stu-id="7d5b3-110">Suggestion</span></span>

<span data-ttu-id="7d5b3-111">.NET Framework 4.7.1 ' ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="7d5b3-111">Upgrade to .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="7d5b3-112">Name</span><span class="sxs-lookup"><span data-stu-id="7d5b3-112">Name</span></span>    | <span data-ttu-id="7d5b3-113">Değer</span><span class="sxs-lookup"><span data-stu-id="7d5b3-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7d5b3-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7d5b3-114">Scope</span></span>   |<span data-ttu-id="7d5b3-115">İkincil</span><span class="sxs-lookup"><span data-stu-id="7d5b3-115">Minor</span></span>|
|<span data-ttu-id="7d5b3-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7d5b3-116">Version</span></span>|<span data-ttu-id="7d5b3-117">4,7</span><span class="sxs-lookup"><span data-stu-id="7d5b3-117">4.7</span></span>|
|<span data-ttu-id="7d5b3-118">Tür</span><span class="sxs-lookup"><span data-stu-id="7d5b3-118">Type</span></span>|<span data-ttu-id="7d5b3-119">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7d5b3-119">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7d5b3-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7d5b3-120">Affected APIs</span></span>

<span data-ttu-id="7d5b3-121">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="7d5b3-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
