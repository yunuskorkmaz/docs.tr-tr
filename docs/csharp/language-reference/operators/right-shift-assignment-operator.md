---
title: '&gt;&gt;= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 02a9559a5c4086eeed09094c15c3620366ffad8c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333700"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="f7d44-102">&gt;&gt;= işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f7d44-102">&gt;&gt;= operator (C# Reference)</span></span>

<span data-ttu-id="f7d44-103">Sağa kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="f7d44-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7d44-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7d44-104">Remarks</span></span>

<span data-ttu-id="f7d44-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="f7d44-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="f7d44-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="f7d44-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="f7d44-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7d44-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f7d44-108">[>> İşleci](right-shift-operator.md) kaydırır `x` sağ tarafından belirtilen bir miktara göre `y`.</span><span class="sxs-lookup"><span data-stu-id="f7d44-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="f7d44-109">>> = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [>> işleci](right-shift-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f7d44-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="f7d44-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7d44-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="f7d44-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7d44-111">See also</span></span>

- [<span data-ttu-id="f7d44-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7d44-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f7d44-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f7d44-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f7d44-114">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="f7d44-114">C# operators</span></span>](index.md)