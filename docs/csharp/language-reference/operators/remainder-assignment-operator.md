---
title: '% = İşleç - C# başvurusu'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245567"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f4baa-102">%= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f4baa-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="f4baa-103">Kalan atama işleci.</span><span class="sxs-lookup"><span data-stu-id="f4baa-103">The remainder assignment operator.</span></span>

<span data-ttu-id="f4baa-104">Bir ifade kullanarak `%=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="f4baa-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="f4baa-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="f4baa-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="f4baa-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f4baa-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="f4baa-107">[Kalan işleci](remainder-operator.md) `%` işlenenleri bir bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f4baa-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="f4baa-108">Tüm sayısal türler tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f4baa-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="f4baa-109">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [kalan işleci](remainder-operator.md) `%`, kalan atama işleci `%=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="f4baa-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="f4baa-110">Aşağıdaki örnek, kullanımını gösterir. `%=` işleci:</span><span class="sxs-lookup"><span data-stu-id="f4baa-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="f4baa-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4baa-111">See also</span></span>

- [<span data-ttu-id="f4baa-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f4baa-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f4baa-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f4baa-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f4baa-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f4baa-114">C# Operators</span></span>](index.md)
