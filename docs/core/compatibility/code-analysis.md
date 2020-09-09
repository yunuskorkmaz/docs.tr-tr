---
title: Kod Analizi bozan değişiklikler
description: .NET kaynak kodu Çözümleyicileri 'ndeki son değişiklikleri listeler.
ms.date: 09/02/2020
ms.openlocfilehash: f1e89c90e6d91b9b3555542a0c7adf2607a76a01
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598050"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="4ea0c-103">Kod Analizi bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="4ea0c-103">Code analysis breaking changes</span></span>

<span data-ttu-id="4ea0c-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="4ea0c-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4ea0c-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="4ea0c-105">Breaking change</span></span> | <span data-ttu-id="4ea0c-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4ea0c-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="4ea0c-107">P/Invoke için String parametresinde CA1417: OutAttribute</span><span class="sxs-lookup"><span data-stu-id="4ea0c-107">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="4ea0c-108">5.0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-108">5.0</span></span> |
| [<span data-ttu-id="4ea0c-109">CA1831: dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın</span><span class="sxs-lookup"><span data-stu-id="4ea0c-109">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="4ea0c-110">5.0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-110">5.0</span></span> |
| [<span data-ttu-id="4ea0c-111">CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın</span><span class="sxs-lookup"><span data-stu-id="4ea0c-111">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="4ea0c-112">5.0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-112">5.0</span></span> |
| [<span data-ttu-id="4ea0c-113">CA2014: Döngülerde stackalloc kullanmayın</span><span class="sxs-lookup"><span data-stu-id="4ea0c-113">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="4ea0c-114">5.0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-114">5.0</span></span> |
| [<span data-ttu-id="4ea0c-115">CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="4ea0c-115">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="4ea0c-116">5.0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-116">5.0</span></span> |
| [<span data-ttu-id="4ea0c-117">CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır</span><span class="sxs-lookup"><span data-stu-id="4ea0c-117">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="4ea0c-118">5.0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="4ea0c-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="4ea0c-119">.NET 5.0</span></span>

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
