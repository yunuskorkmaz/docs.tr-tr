---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614667"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a><span data-ttu-id="ca6e6-101">Görevler arasında CurrentCulture ve CurrentUICulture Flow</span><span class="sxs-lookup"><span data-stu-id="ca6e6-101">CurrentCulture and CurrentUICulture flow across tasks</span></span>

#### <a name="details"></a><span data-ttu-id="ca6e6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ca6e6-102">Details</span></span>

<span data-ttu-id="ca6e6-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> <xref:System.Threading.ExecutionContext?displayProperty=fullName> zaman uyumsuz işlemler arasında akan iş parçacığında saklanır. Bu, veya üzerindeki değişikliklerin <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> , daha sonra zaman uyumsuz olarak çalıştırılan görevlerde yansıtıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca6e6-103">Beginning in the .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> are stored in the thread's <xref:System.Threading.ExecutionContext?displayProperty=fullName>, which flows across asynchronous operations.This means that changes to <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> will be reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="ca6e6-104">Bu, önceki .NET Framework sürümlerinin davranışından (yani <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> , <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> tüm zaman uyumsuz görevlerde) farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ca6e6-104">This is different from the behavior of previous .NET Framework versions (which would reset <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> in all asynchronous tasks).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca6e6-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="ca6e6-105">Suggestion</span></span>

<span data-ttu-id="ca6e6-106">Bu değişiklikten etkilenen uygulamalar, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> bir zaman uyumsuz görevde istenen veya ilk işlem olarak açıkça ayarlanarak soruna geçici bir çözüm verebilir.</span><span class="sxs-lookup"><span data-stu-id="ca6e6-106">Apps affected by this change may work around it by explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> as the first operation in an async Task.</span></span> <span data-ttu-id="ca6e6-107">Alternatif olarak, eski davranış (akan değil <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) aşağıdaki uyumluluk anahtarı ayarlanarak kabul edilebilir:</span><span class="sxs-lookup"><span data-stu-id="ca6e6-107">Alternatively, the old behavior (of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) may be opted into by setting the following compatibility switch:</span></span>

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

<span data-ttu-id="ca6e6-108">Bu sorun WPF tarafından .NET Framework 4.6.2 içinde düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="ca6e6-108">This issue has been fixed by WPF in .NET Framework 4.6.2.</span></span> <span data-ttu-id="ca6e6-109">Ayrıca, .NET Framework 4,6 ' de 4.6.1 ile [KB 3139549](https://support.microsoft.com/kb/3139549)arasında düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca6e6-109">It has also been fixed in .NET Frameworks 4.6, 4.6.1 through [KB 3139549](https://support.microsoft.com/kb/3139549).</span></span> <span data-ttu-id="ca6e6-110">.NET Framework 4,6 veya sonraki bir sürümü hedefleyen uygulamalar, otomatik olarak WPF uygulamalarında doğru davranış alır- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) dağıtıcı işlemleri genelinde korunacaktır.</span><span class="sxs-lookup"><span data-stu-id="ca6e6-110">Applications targeting .NET Framework 4.6 or later will automatically get the right behavior in WPF applications - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) would be preserved across Dispatcher operations.</span></span>

| <span data-ttu-id="ca6e6-111">Name</span><span class="sxs-lookup"><span data-stu-id="ca6e6-111">Name</span></span>    | <span data-ttu-id="ca6e6-112">Değer</span><span class="sxs-lookup"><span data-stu-id="ca6e6-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca6e6-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ca6e6-113">Scope</span></span>   | <span data-ttu-id="ca6e6-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="ca6e6-114">Minor</span></span>       |
| <span data-ttu-id="ca6e6-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ca6e6-115">Version</span></span> | <span data-ttu-id="ca6e6-116">4.6</span><span class="sxs-lookup"><span data-stu-id="ca6e6-116">4.6</span></span>         |
| <span data-ttu-id="ca6e6-117">Tür</span><span class="sxs-lookup"><span data-stu-id="ca6e6-117">Type</span></span>    | <span data-ttu-id="ca6e6-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="ca6e6-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ca6e6-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ca6e6-119">Affected APIs</span></span>

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
