---
title: Kod Analizi bozan değişiklikler
description: .NET kaynak kodu Çözümleyicileri 'ndeki son değişiklikleri listeler.
ms.date: 09/02/2020
ms.openlocfilehash: 3cbe2ecf5d08084db542db0c2da016f1f391452e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538935"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="188a3-103">Kod Analizi bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="188a3-103">Code analysis breaking changes</span></span>

<span data-ttu-id="188a3-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="188a3-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="188a3-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="188a3-105">Breaking change</span></span> | <span data-ttu-id="188a3-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="188a3-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="188a3-107">CA1416: platform uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="188a3-107">CA1416: Platform compatibility</span></span>](#ca1416-platform-compatibility) | <span data-ttu-id="188a3-108">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-108">5.0</span></span> |
| [<span data-ttu-id="188a3-109">P/Invoke için String parametresinde CA1417: OutAttribute</span><span class="sxs-lookup"><span data-stu-id="188a3-109">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="188a3-110">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-110">5.0</span></span> |
| [<span data-ttu-id="188a3-111">CA1831: dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın</span><span class="sxs-lookup"><span data-stu-id="188a3-111">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="188a3-112">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-112">5.0</span></span> |
| [<span data-ttu-id="188a3-113">CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın</span><span class="sxs-lookup"><span data-stu-id="188a3-113">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="188a3-114">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-114">5.0</span></span> |
| [<span data-ttu-id="188a3-115">CA2014: Döngülerde stackalloc kullanmayın</span><span class="sxs-lookup"><span data-stu-id="188a3-115">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="188a3-116">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-116">5.0</span></span> |
| [<span data-ttu-id="188a3-117">CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="188a3-117">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="188a3-118">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-118">5.0</span></span> |
| [<span data-ttu-id="188a3-119">CA2200: Yığın ayrıntılarını korumak için yeniden fırlatın</span><span class="sxs-lookup"><span data-stu-id="188a3-119">CA2200: Rethrow to preserve stack details</span></span>](#ca2200-rethrow-to-preserve-stack-details) | <span data-ttu-id="188a3-120">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-120">5.0</span></span> |
| [<span data-ttu-id="188a3-121">CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır</span><span class="sxs-lookup"><span data-stu-id="188a3-121">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="188a3-122">5.0</span><span class="sxs-lookup"><span data-stu-id="188a3-122">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="188a3-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="188a3-123">.NET 5.0</span></span>

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ca2200-rethrow-to-preserve-stack-details](../../../includes/core-changes/codeanalysis/5.0/ca2200-rethrow-to-preserve-stack-details.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
