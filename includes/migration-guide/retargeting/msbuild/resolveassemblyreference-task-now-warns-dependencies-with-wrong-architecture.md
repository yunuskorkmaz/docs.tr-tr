---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616099"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="37ece-101">ResolveAssemblyReference görevi artık yanlış mimariye sahip bağımlılıkları uyarır</span><span class="sxs-lookup"><span data-stu-id="37ece-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="37ece-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="37ece-102">Details</span></span>

<span data-ttu-id="37ece-103">Görev bir uyarı yayar, bu, bir başvurunun veya bağımlılıklarından birinin uygulamanın mimarisiyle eşleşmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37ece-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="37ece-104">Örneğin, seçeneğiyle derlenen bir uygulama `AnyCPU` bir x86 başvurusu içeriyorsa bu durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="37ece-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="37ece-105">Bu tür bir senaryo, çalışma zamanında bir uygulama hatasına neden olabilir (Bu durumda, uygulama bir x64 işlemi olarak dağıtılırsa).</span><span class="sxs-lookup"><span data-stu-id="37ece-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="37ece-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="37ece-106">Suggestion</span></span>

<span data-ttu-id="37ece-107">İki etki alanı vardır:</span><span class="sxs-lookup"><span data-stu-id="37ece-107">There are two areas of impact:</span></span>

- <span data-ttu-id="37ece-108">Yeniden derleme, uygulama MSBuild 'in önceki bir sürümü altında derlenmişse görünmeyen uyarılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37ece-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="37ece-109">Ancak, uyarı bir çalışma zamanı hatası kaynağını tanımladığından, araştırılması ve giderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="37ece-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="37ece-110">Uyarılar hata olarak kabul edilir, uygulama derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="37ece-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="37ece-111">Name</span><span class="sxs-lookup"><span data-stu-id="37ece-111">Name</span></span>    | <span data-ttu-id="37ece-112">Değer</span><span class="sxs-lookup"><span data-stu-id="37ece-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="37ece-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="37ece-113">Scope</span></span>   | <span data-ttu-id="37ece-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="37ece-114">Minor</span></span>       |
| <span data-ttu-id="37ece-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="37ece-115">Version</span></span> | <span data-ttu-id="37ece-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="37ece-116">4.5.1</span></span>       |
| <span data-ttu-id="37ece-117">Tür</span><span class="sxs-lookup"><span data-stu-id="37ece-117">Type</span></span>    | <span data-ttu-id="37ece-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="37ece-118">Retargeting</span></span> |
