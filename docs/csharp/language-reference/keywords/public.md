---
title: public anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 84a3bc49b6eea047d518edc01dab7f2301854b6a
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256134"
---
# <a name="public-c-reference"></a><span data-ttu-id="b275c-102">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b275c-102">public (C# Reference)</span></span>

<span data-ttu-id="b275c-103">`public` Anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="b275c-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="b275c-104">Genel erişim, en esnek erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="b275c-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="b275c-105">Bu örnekte olduğu gibi public üyelere erişmede hiçbir kısıtlama vardır:</span><span class="sxs-lookup"><span data-stu-id="b275c-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="b275c-106">Bkz: [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md) ve [erişilebilirlik düzeyleri](accessibility-levels.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="b275c-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="b275c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b275c-107">Example</span></span>

<span data-ttu-id="b275c-108">Aşağıdaki örnekte, iki sınıf bildirilen, `PointTest` ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="b275c-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="b275c-109">Genel üyeleri `x` ve `y` , `PointTest` doğrudan erişilir `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="b275c-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="b275c-110">Değiştirirseniz `public` erişim düzeyi için [özel](private.md) veya [korumalı](protected.md), hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="b275c-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="b275c-111">'PointTest.y' koruma düzeyi nedeniyle erişilemez durumda.</span><span class="sxs-lookup"><span data-stu-id="b275c-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b275c-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b275c-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b275c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b275c-113">See also</span></span>

- [<span data-ttu-id="b275c-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b275c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b275c-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b275c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b275c-116">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b275c-116">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="b275c-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b275c-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b275c-118">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b275c-118">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="b275c-119">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b275c-119">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="b275c-120">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b275c-120">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="b275c-121">private</span><span class="sxs-lookup"><span data-stu-id="b275c-121">private</span></span>](private.md)
- [<span data-ttu-id="b275c-122">protected</span><span class="sxs-lookup"><span data-stu-id="b275c-122">protected</span></span>](protected.md)
- [<span data-ttu-id="b275c-123">internal</span><span class="sxs-lookup"><span data-stu-id="b275c-123">internal</span></span>](internal.md)