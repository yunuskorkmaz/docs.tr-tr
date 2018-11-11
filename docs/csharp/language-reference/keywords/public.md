---
title: public anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: b2e09bdb16d6128d69a3eb33cf2cffd4cba60376
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43518192"
---
# <a name="public-c-reference"></a><span data-ttu-id="59993-102">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="59993-102">public (C# Reference)</span></span>

<span data-ttu-id="59993-103">`public` Anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="59993-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="59993-104">Genel erişim, en esnek erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="59993-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="59993-105">Bu örnekte olduğu gibi public üyelere erişmede hiçbir kısıtlama vardır:</span><span class="sxs-lookup"><span data-stu-id="59993-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="59993-106">Bkz: [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md) ve [erişilebilirlik düzeyleri](accessibility-levels.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="59993-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="59993-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="59993-107">Example</span></span>

<span data-ttu-id="59993-108">Aşağıdaki örnekte, iki sınıf bildirilen, `PointTest` ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="59993-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="59993-109">Genel üyeleri `x` ve `y` , `PointTest` doğrudan erişilir `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="59993-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="59993-110">Değiştirirseniz `public` erişim düzeyi için [özel](private.md) veya [korumalı](protected.md), hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="59993-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="59993-111">'PointTest.y' koruma düzeyi nedeniyle erişilemez durumda.</span><span class="sxs-lookup"><span data-stu-id="59993-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59993-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="59993-112">C# language specification</span></span>  

<span data-ttu-id="59993-113">Daha fazla bilgi için [erişilebilirlik bildirilen](~/_csharplang/spec/basic-concepts.md#declared-accessibility) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="59993-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="59993-114">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="59993-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="59993-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59993-115">See also</span></span>

- [<span data-ttu-id="59993-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="59993-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="59993-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="59993-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="59993-118">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="59993-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="59993-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="59993-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="59993-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="59993-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="59993-121">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="59993-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="59993-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="59993-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="59993-123">private</span><span class="sxs-lookup"><span data-stu-id="59993-123">private</span></span>](private.md)
- [<span data-ttu-id="59993-124">protected</span><span class="sxs-lookup"><span data-stu-id="59993-124">protected</span></span>](protected.md)
- [<span data-ttu-id="59993-125">internal</span><span class="sxs-lookup"><span data-stu-id="59993-125">internal</span></span>](internal.md)