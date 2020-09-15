---
title: Kod Analizi bozan değişiklikler
description: .NET kaynak kodu Çözümleyicileri 'ndeki son değişiklikleri listeler.
ms.date: 09/02/2020
ms.openlocfilehash: 20badd69b316e1d87700b3c5061a71d648b71c64
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065200"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="c06ec-103">Kod Analizi bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="c06ec-103">Code analysis breaking changes</span></span>

<span data-ttu-id="c06ec-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="c06ec-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c06ec-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="c06ec-105">Breaking change</span></span> | <span data-ttu-id="c06ec-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c06ec-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c06ec-107">CA1416: platform uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="c06ec-107">CA1416: Platform compatibility</span></span>](#ca1416-platform-compatibility) | <span data-ttu-id="c06ec-108">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-108">5.0</span></span> |
| [<span data-ttu-id="c06ec-109">P/Invoke için String parametresinde CA1417: OutAttribute</span><span class="sxs-lookup"><span data-stu-id="c06ec-109">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="c06ec-110">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-110">5.0</span></span> |
| [<span data-ttu-id="c06ec-111">CA1831: dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın</span><span class="sxs-lookup"><span data-stu-id="c06ec-111">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="c06ec-112">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-112">5.0</span></span> |
| [<span data-ttu-id="c06ec-113">CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın</span><span class="sxs-lookup"><span data-stu-id="c06ec-113">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="c06ec-114">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-114">5.0</span></span> |
| [<span data-ttu-id="c06ec-115">CA2014: Döngülerde stackalloc kullanmayın</span><span class="sxs-lookup"><span data-stu-id="c06ec-115">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="c06ec-116">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-116">5.0</span></span> |
| [<span data-ttu-id="c06ec-117">CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="c06ec-117">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="c06ec-118">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-118">5.0</span></span> |
| [<span data-ttu-id="c06ec-119">CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır</span><span class="sxs-lookup"><span data-stu-id="c06ec-119">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="c06ec-120">5.0</span><span class="sxs-lookup"><span data-stu-id="c06ec-120">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c06ec-121">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c06ec-121">.NET 5.0</span></span>

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

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
