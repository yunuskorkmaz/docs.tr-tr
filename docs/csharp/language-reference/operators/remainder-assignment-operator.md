---
title: '%= İşleci (C# Başvurusu)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738294"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0a338-102">%= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0a338-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="0a338-103">Kalan atama işleci.</span><span class="sxs-lookup"><span data-stu-id="0a338-103">The remainder assignment operator.</span></span>

<span data-ttu-id="0a338-104">Bir ifade kullanarak `%=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="0a338-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="0a338-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="0a338-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="0a338-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0a338-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="0a338-107">[Kalan işleci](remainder-operator.md) `%` tüm sayısal türler tarafından desteklenir ve işlenenleri bir bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="0a338-107">The [remainder operator](remainder-operator.md) `%` is supported by all numeric types and computes the remainder after division of its operands.</span></span>

<span data-ttu-id="0a338-108">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [kalan işleci](remainder-operator.md) `%`, kalan atama işleci `%=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="0a338-108">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="0a338-109">Aşağıdaki örnek, kullanımını gösterir. `%=` işleci:</span><span class="sxs-lookup"><span data-stu-id="0a338-109">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="0a338-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a338-110">See also</span></span>

- [<span data-ttu-id="0a338-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0a338-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0a338-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a338-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0a338-113">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0a338-113">C# Operators</span></span>](index.md)
