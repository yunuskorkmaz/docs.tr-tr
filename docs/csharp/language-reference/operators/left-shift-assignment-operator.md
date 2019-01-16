---
title: '&lt;&lt;= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333258"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="4369c-102">&lt;&lt;= işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4369c-102">&lt;&lt;= operator (C# Reference)</span></span>

<span data-ttu-id="4369c-103">Sola kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="4369c-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="4369c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4369c-104">Remarks</span></span>

<span data-ttu-id="4369c-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="4369c-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="4369c-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="4369c-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="4369c-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4369c-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4369c-108">[<< İşleci](left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı kadar sola `y`.</span><span class="sxs-lookup"><span data-stu-id="4369c-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="4369c-109">`<<=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](left-shift-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4369c-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="4369c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4369c-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="4369c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4369c-111">See also</span></span>

- [<span data-ttu-id="4369c-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4369c-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4369c-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4369c-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4369c-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="4369c-114">C# Operators</span></span>](index.md)
