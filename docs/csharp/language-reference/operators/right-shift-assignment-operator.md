---
title: '>>= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278986"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aa0a4-102">>> = işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aa0a4-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="aa0a4-103">Sağa kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="aa0a4-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa0a4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa0a4-104">Remarks</span></span>

<span data-ttu-id="aa0a4-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="aa0a4-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="aa0a4-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="aa0a4-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="aa0a4-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aa0a4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="aa0a4-108">[>> İşleci](right-shift-operator.md) kaydırır `x` sağ tarafından belirtilen bir miktara göre `y`.</span><span class="sxs-lookup"><span data-stu-id="aa0a4-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="aa0a4-109">>> = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [>> işleci](right-shift-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="aa0a4-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="aa0a4-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa0a4-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="aa0a4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa0a4-111">See also</span></span>

- [<span data-ttu-id="aa0a4-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa0a4-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aa0a4-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa0a4-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aa0a4-114">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="aa0a4-114">C# operators</span></span>](index.md)