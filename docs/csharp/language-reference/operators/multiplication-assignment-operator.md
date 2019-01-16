---
title: '* = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333440"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c84c9-102">\*= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c84c9-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="c84c9-103">İkili çarpma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="c84c9-103">The binary multiplication assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="c84c9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c84c9-104">Remarks</span></span>

<span data-ttu-id="c84c9-105">Bir ifade kullanarak `*=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="c84c9-105">An expression using the `*=` assignment operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="c84c9-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="c84c9-106">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="c84c9-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c84c9-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="c84c9-108">[ \* İşleci](multiplication-operator.md) çarpma işlemi gerçekleştirmek sayısal türleri için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="c84c9-108">The [\* operator](multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>

<span data-ttu-id="c84c9-109">`*=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [ \* işleci](multiplication-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c84c9-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](multiplication-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="c84c9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c84c9-110">Example</span></span>

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a><span data-ttu-id="c84c9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c84c9-111">See also</span></span>

- [<span data-ttu-id="c84c9-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c84c9-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c84c9-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c84c9-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c84c9-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c84c9-114">C# Operators</span></span>](index.md)
