---
title: '%= İşleci (C# Başvurusu)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188722"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8701f-102">%= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8701f-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="8701f-103">Kalan atama işleci.</span><span class="sxs-lookup"><span data-stu-id="8701f-103">The remainder assignment operator.</span></span>

<span data-ttu-id="8701f-104">Bir ifade kullanarak `%=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="8701f-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="8701f-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="8701f-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="8701f-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8701f-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="8701f-107">[Kalan işleci](remainder-operator.md) `%` işlenenleri bir bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8701f-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="8701f-108">Tüm sayısal türler tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8701f-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="8701f-109">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [kalan işleci](remainder-operator.md) `%`, kalan atama işleci `%=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="8701f-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="8701f-110">Aşağıdaki örnek, kullanımını gösterir. `%=` işleci:</span><span class="sxs-lookup"><span data-stu-id="8701f-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="8701f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8701f-111">See also</span></span>

- [<span data-ttu-id="8701f-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8701f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8701f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8701f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8701f-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8701f-114">C# Operators</span></span>](index.md)
