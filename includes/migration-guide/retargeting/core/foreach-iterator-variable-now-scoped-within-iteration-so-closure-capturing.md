---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617274"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="fe11b-101">Foreach Yineleyici değişkeni artık yineleme içinde kapsamlandırılır, bu nedenle kapatma yakalama semantiği farklıdır (C# 5 ' te)</span><span class="sxs-lookup"><span data-stu-id="fe11b-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="fe11b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fe11b-102">Details</span></span>

<span data-ttu-id="fe11b-103">C# 5 ' ten itibaren (Visual Studio 2012), `foreach` Yineleyici değişkenleri yineleme içinde kapsamlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fe11b-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="fe11b-104">Bu, kodun daha önce kendi kapanışına dahil edilmez olan değişkenlere bağlı olması durumunda kesintiler oluşmasına neden olabilir `foreach` .</span><span class="sxs-lookup"><span data-stu-id="fe11b-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="fe11b-105">Bu değişikliğin belirtisi, bir temsilciye geçirilen bir yineleyici değişkeninin, temsilcinin çağrıldığı zaman değeri yerine temsilci oluşturulduğu sırada sahip olduğu değer olarak değerlendirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="fe11b-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe11b-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="fe11b-106">Suggestion</span></span>

<span data-ttu-id="fe11b-107">İdeal olarak, kodun yeni derleyici davranışını beklediği için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe11b-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="fe11b-108">Eski semantikler gerekliyse, yineleyici değişkeni, açıkça döngünün kapsamının dışına yerleştirilmiş olan ayrı bir değişkenle değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe11b-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="fe11b-109">Name</span><span class="sxs-lookup"><span data-stu-id="fe11b-109">Name</span></span>    | <span data-ttu-id="fe11b-110">Değer</span><span class="sxs-lookup"><span data-stu-id="fe11b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fe11b-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fe11b-111">Scope</span></span>   | <span data-ttu-id="fe11b-112">Ana</span><span class="sxs-lookup"><span data-stu-id="fe11b-112">Major</span></span>       |
| <span data-ttu-id="fe11b-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fe11b-113">Version</span></span> | <span data-ttu-id="fe11b-114">4,5</span><span class="sxs-lookup"><span data-stu-id="fe11b-114">4.5</span></span>         |
| <span data-ttu-id="fe11b-115">Tür</span><span class="sxs-lookup"><span data-stu-id="fe11b-115">Type</span></span>    | <span data-ttu-id="fe11b-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="fe11b-116">Retargeting</span></span> |
