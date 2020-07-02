---
ms.openlocfilehash: c557f1cb65a675446bc77c57ef91972df92712bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617256"
---
### <a name="iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a><span data-ttu-id="885f1-101">Sonuç görevinin tamamlanabilmesi için IAsyncResult. CompletedSynchronously özelliğinin doğru olması gerekir</span><span class="sxs-lookup"><span data-stu-id="885f1-101">IAsyncResult.CompletedSynchronously property must be correct for the resulting task to complete</span></span>

#### <a name="details"></a><span data-ttu-id="885f1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="885f1-102">Details</span></span>

<span data-ttu-id="885f1-103">TaskFactory. FromAsync çağrılırken, <xref:System.IAsyncResult.CompletedSynchronously> sonuçta elde edilen görevin tamamlanabilmesi için özelliğin uygulanması doğru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="885f1-103">When calling TaskFactory.FromAsync, the implementation of the <xref:System.IAsyncResult.CompletedSynchronously> property must be correct for the resulting task to complete.</span></span> <span data-ttu-id="885f1-104">Diğer bir deyişle, özelliğinin true döndürmesi gerekir ve yalnızca uygulama eşzamanlı olarak tamamlanırsa.</span><span class="sxs-lookup"><span data-stu-id="885f1-104">That is, the property must return true if, and only if, the implementation completed synchronously.</span></span> <span data-ttu-id="885f1-105">Daha önce özellik denetlenmedi.</span><span class="sxs-lookup"><span data-stu-id="885f1-105">Previously, the property was not checked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="885f1-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="885f1-106">Suggestion</span></span>

<span data-ttu-id="885f1-107"><xref:System.IAsyncResult?displayProperty=fullName>Uygulamalar, <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> yalnızca bir görev zaman uyumlu olarak tamamlandığında özellik için doğru true olarak döndürülirse hiçbir kesme gözlemlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="885f1-107">If <xref:System.IAsyncResult?displayProperty=fullName> implementations correctly return true for the <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> property only when a task completed synchronously, then no break will be observed.</span></span> <span data-ttu-id="885f1-108">Kullanıcılar <xref:System.IAsyncResult?displayProperty=fullName> , bir görevin zaman uyumlu olarak tamamlanıp tamamlanmadığını doğru şekilde değerlendirdiğinden emin olmak için sahip oldukları uygulamaları (varsa) gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="885f1-108">Users should review <xref:System.IAsyncResult?displayProperty=fullName> implementations they own (if any) to ensure that they correctly evaluate whether a task completed synchronously or not.</span></span>

| <span data-ttu-id="885f1-109">Name</span><span class="sxs-lookup"><span data-stu-id="885f1-109">Name</span></span>    | <span data-ttu-id="885f1-110">Değer</span><span class="sxs-lookup"><span data-stu-id="885f1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="885f1-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="885f1-111">Scope</span></span>   | <span data-ttu-id="885f1-112">Edge</span><span class="sxs-lookup"><span data-stu-id="885f1-112">Edge</span></span>        |
| <span data-ttu-id="885f1-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="885f1-113">Version</span></span> | <span data-ttu-id="885f1-114">4,5</span><span class="sxs-lookup"><span data-stu-id="885f1-114">4.5</span></span>         |
| <span data-ttu-id="885f1-115">Tür</span><span class="sxs-lookup"><span data-stu-id="885f1-115">Type</span></span>    | <span data-ttu-id="885f1-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="885f1-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="885f1-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="885f1-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
