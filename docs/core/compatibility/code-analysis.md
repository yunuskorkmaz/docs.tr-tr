---
title: Kod Analizi bozan değişiklikler
description: .NET kaynak kodu Çözümleyicileri 'ndeki son değişiklikleri listeler.
ms.date: 08/22/2020
ms.openlocfilehash: 8b2b50c5f03a3ca971aefd0f2cf53624dfa82274
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465601"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="c7b24-103">Kod Analizi bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="c7b24-103">Code analysis breaking changes</span></span>

<span data-ttu-id="c7b24-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="c7b24-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c7b24-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="c7b24-105">Breaking change</span></span> | <span data-ttu-id="c7b24-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c7b24-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c7b24-107">CA1831: Aralık tabanlı dizin oluşturucu yerine AsSpan veya AsMemory kullanın</span><span class="sxs-lookup"><span data-stu-id="c7b24-107">CA1831: Use AsSpan or AsMemory instead of Range-based indexer</span></span>](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | <span data-ttu-id="c7b24-108">5.0</span><span class="sxs-lookup"><span data-stu-id="c7b24-108">5.0</span></span> |
| [<span data-ttu-id="c7b24-109">CA2014: Döngülerde stackalloc kullanmayın</span><span class="sxs-lookup"><span data-stu-id="c7b24-109">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="c7b24-110">5.0</span><span class="sxs-lookup"><span data-stu-id="c7b24-110">5.0</span></span> |
| [<span data-ttu-id="c7b24-111">CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="c7b24-111">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="c7b24-112">5.0</span><span class="sxs-lookup"><span data-stu-id="c7b24-112">5.0</span></span> |
| [<span data-ttu-id="c7b24-113">CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır</span><span class="sxs-lookup"><span data-stu-id="c7b24-113">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="c7b24-114">5.0</span><span class="sxs-lookup"><span data-stu-id="c7b24-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c7b24-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7b24-115">.NET 5.0</span></span>

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
