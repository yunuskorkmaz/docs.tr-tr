---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144493"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="4d713-101">CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur</span><span class="sxs-lookup"><span data-stu-id="4d713-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="4d713-102">.NET 5,0 ' den başlayarak, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> sayaç kümesi zaten varsa bir yerine bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d713-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4d713-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4d713-103">Change description</span></span>

<span data-ttu-id="4d713-104">.NET Framework ve .NET Core 1,0 ile 3,1 arasında, çağırarak sayaç kümesinin bir örneğini oluşturabilirsiniz <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="4d713-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="4d713-105">Ancak, sayaç kümesi zaten varsa, yöntem bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d713-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="4d713-106">.NET 5,0 ve sonraki sürümlerinde, çağırdığınızda <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ve sayaç kümesi varsa, bir <xref:System.InvalidOperationException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d713-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4d713-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4d713-107">Version introduced</span></span>

<span data-ttu-id="4d713-108">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="4d713-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4d713-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4d713-109">Recommended action</span></span>

<span data-ttu-id="4d713-110"><xref:System.ArgumentException>Çağrılırken uygulamanızda özel durumları yakalarsanız <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> özel durumları da yakalamaya göz önünde bulundurun <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="4d713-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="4d713-111">Yakalama <xref:System.ArgumentException> özel durumları önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4d713-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="4d713-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="4d713-112">Category</span></span>

<span data-ttu-id="4d713-113">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="4d713-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4d713-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4d713-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
