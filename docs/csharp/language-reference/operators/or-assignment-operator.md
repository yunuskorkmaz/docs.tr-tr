---
title: '| = İşleç - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333271"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e0572-102">| = işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0572-102">|= operator (C# Reference)</span></span>

<span data-ttu-id="e0572-103">OR atama işleci.</span><span class="sxs-lookup"><span data-stu-id="e0572-103">The OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0572-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0572-104">Remarks</span></span>

<span data-ttu-id="e0572-105">Bir ifade kullanarak `|=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="e0572-105">An expression using the `|=` assignment operator, such as</span></span>

```csharp
x |= y
```

<span data-ttu-id="e0572-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="e0572-106">is equivalent to</span></span>

```csharp
x = x | y
```

<span data-ttu-id="e0572-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e0572-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e0572-108">[ &#124; İşleci](or-operator.md) bool işlenenlerde integral işlenen üzerinde bit düzeyinde bir mantıksal OR işlem ve mantıksal OR gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e0572-108">The [&#124; operator](or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>

<span data-ttu-id="e0572-109">`|=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [ &#124; işleci](or-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e0572-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](or-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="e0572-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0572-110">Example</span></span>

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a><span data-ttu-id="e0572-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0572-111">See also</span></span>

- [<span data-ttu-id="e0572-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0572-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0572-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0572-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0572-114">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="e0572-114">C# operators</span></span>](index.md)