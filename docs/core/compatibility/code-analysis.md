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
# <a name="code-analysis-breaking-changes"></a>Kod Analizi bozan değişiklikler

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [P/Invoke için String parametresinde CA1417: OutAttribute](#ca1417-outattribute-on-string-parameter-for-pinvoke) | 5.0 |
| [CA1831: dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | 5.0 |
| [CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın](#ca2013-do-not-use-referenceequals-with-value-types) | 5.0 |
| [CA2014: Döngülerde stackalloc kullanmayın](#ca2014-do-not-use-stackalloc-in-loops) | 5.0 |
| [CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5.0 |
| [CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5.0 |

## <a name="net-50"></a>.NET 5,0

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
