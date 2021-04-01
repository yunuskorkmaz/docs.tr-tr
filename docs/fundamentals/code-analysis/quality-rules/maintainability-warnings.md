---
title: Bakım kuralları (kod analizi)
description: Kod Analizi bakım kuralları hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588820"
---
# <a name="maintainability-rules"></a><span data-ttu-id="e8850-103">Bakım kuralları</span><span class="sxs-lookup"><span data-stu-id="e8850-103">Maintainability rules</span></span>

<span data-ttu-id="e8850-104">Bakımlama kuralları kitaplığı ve uygulama bakımını destekler.</span><span class="sxs-lookup"><span data-stu-id="e8850-104">Maintainability rules support library and application maintenance.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e8850-105">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="e8850-105">In this section</span></span>

| <span data-ttu-id="e8850-106">Kural</span><span class="sxs-lookup"><span data-stu-id="e8850-106">Rule</span></span> | <span data-ttu-id="e8850-107">Description</span><span class="sxs-lookup"><span data-stu-id="e8850-107">Description</span></span> |
|-----------|-----------------------------------|
| [<span data-ttu-id="e8850-108">CA1501: Aşırı devralmadan kaçının</span><span class="sxs-lookup"><span data-stu-id="e8850-108">CA1501: Avoid excessive inheritance</span></span>](ca1501.md) | <span data-ttu-id="e8850-109">Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür.</span><span class="sxs-lookup"><span data-stu-id="e8850-109">A type is more than four levels deep in its inheritance hierarchy.</span></span> <span data-ttu-id="e8850-110">İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8850-110">Deeply nested type hierarchies can be difficult to follow, understand, and maintain.</span></span> |
| [<span data-ttu-id="e8850-111">CA1502: Aşırı karmaşıklıktan kaçının</span><span class="sxs-lookup"><span data-stu-id="e8850-111">CA1502: Avoid excessive complexity</span></span>](ca1502.md) | <span data-ttu-id="e8850-112">Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer.</span><span class="sxs-lookup"><span data-stu-id="e8850-112">This rule measures the number of linearly independent paths through the method, which is determined by the number and complexity of conditional branches.</span></span> |
| [<span data-ttu-id="e8850-113">CA1505: Bakımı yapılamayan kodlardan kaçının</span><span class="sxs-lookup"><span data-stu-id="e8850-113">CA1505: Avoid unmaintainable code</span></span>](ca1505.md) | <span data-ttu-id="e8850-114">Bir tür veya yöntemin düşük bakım dizin değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="e8850-114">A type or method has a low maintainability index value.</span></span> <span data-ttu-id="e8850-115">Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="e8850-115">A low maintainability index indicates that a type or method is probably difficult to maintain and would be a good candidate for redesign.</span></span> |
| [<span data-ttu-id="e8850-116">CA1506: Aşırı sınıf bağlantısından kaçının</span><span class="sxs-lookup"><span data-stu-id="e8850-116">CA1506: Avoid excessive class coupling</span></span>](ca1506.md) | <span data-ttu-id="e8850-117">Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer.</span><span class="sxs-lookup"><span data-stu-id="e8850-117">This rule measures class coupling by counting the number of unique type references that a type or method contains.</span></span> |
| [<span data-ttu-id="e8850-118">CA1507: Dize yerine nameof kullanma</span><span class="sxs-lookup"><span data-stu-id="e8850-118">CA1507: Use nameof in place of string</span></span>](ca1507.md) | <span data-ttu-id="e8850-119">Bir dize sabit değeri, bir ifadenin kullanılabileceği bir bağımsız değişken olarak kullanılır `nameof` .</span><span class="sxs-lookup"><span data-stu-id="e8850-119">A string literal is used as an argument where a `nameof` expression could be used.</span></span> |
| [<span data-ttu-id="e8850-120">CA1508: Ölü koşullu kodlardan kaçının</span><span class="sxs-lookup"><span data-stu-id="e8850-120">CA1508: Avoid dead conditional code</span></span>](ca1508.md) | <span data-ttu-id="e8850-121">Bir yöntemde, her zaman çalışma zamanında olarak değerlendirilen koşullu kod bulunur `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="e8850-121">A method has conditional code that always evaluates to `true` or `false` at runtime.</span></span> <span data-ttu-id="e8850-122">Bu `false` , koşulun dalındaki ölü koda yol açar.</span><span class="sxs-lookup"><span data-stu-id="e8850-122">This leads to dead code in the `false` branch of the condition.</span></span> |
| [<span data-ttu-id="e8850-123">CA1509: Kod ölçümleri yapılandırma dosyasında geçersiz girdi</span><span class="sxs-lookup"><span data-stu-id="e8850-123">CA1509: Invalid entry in code metrics configuration file</span></span>](ca1509.md) | <span data-ttu-id="e8850-124">[CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) ve [CA1506](ca1506.md)gibi kod ölçüm kuralları, geçersiz bir girişi olan adlı bir yapılandırma dosyası sağladı `CodeMetricsConfig.txt` .</span><span class="sxs-lookup"><span data-stu-id="e8850-124">Code metrics rules, such as [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) and [CA1506](ca1506.md), supplied a configuration file named `CodeMetricsConfig.txt` that has an invalid entry.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e8850-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8850-125">See also</span></span>

- [<span data-ttu-id="e8850-126">Yönetilen kodun ölçüm karmaşıklığı ve Bakımma</span><span class="sxs-lookup"><span data-stu-id="e8850-126">Measure Complexity and Maintainability of Managed Code</span></span>](/visualstudio/code-quality/code-metrics-values)
