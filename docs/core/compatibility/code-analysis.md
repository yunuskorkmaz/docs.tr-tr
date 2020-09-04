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
# <a name="code-analysis-breaking-changes"></a>Kod Analizi bozan değişiklikler

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [CA1831: Aralık tabanlı dizin oluşturucu yerine AsSpan veya AsMemory kullanın](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | 5.0 |
| [CA2014: Döngülerde stackalloc kullanmayın](#ca2014-do-not-use-stackalloc-in-loops) | 5.0 |
| [CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5.0 |
| [CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
