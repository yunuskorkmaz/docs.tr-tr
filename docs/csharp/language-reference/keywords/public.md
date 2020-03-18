---
title: ortak anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 19906d7fd0f7d41ef9e4cdaf951c77825e0bbead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713176"
---
# <a name="public-c-reference"></a><span data-ttu-id="8decd-102">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8decd-102">public (C# Reference)</span></span>

<span data-ttu-id="8decd-103">`public` Anahtar kelime, türler ve tür üyeleri için bir erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="8decd-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="8decd-104">Genel erişim en izin verilen erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="8decd-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="8decd-105">Bu örnekte olduğu gibi, herkese açık üyelere erişimkonusunda herhangi bir kısıtlama yoktur:</span><span class="sxs-lookup"><span data-stu-id="8decd-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="8decd-106">Daha fazla bilgi için [Erişim Değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md) ve [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="8decd-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="8decd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8decd-107">Example</span></span>

<span data-ttu-id="8decd-108">Aşağıdaki örnekte, iki sınıf `PointTest` bildirilir `MainClass`ve .</span><span class="sxs-lookup"><span data-stu-id="8decd-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="8decd-109">Kamu üyeleri `x` `y` ve `PointTest` doğrudan `MainClass`erişilir.</span><span class="sxs-lookup"><span data-stu-id="8decd-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="8decd-110">`public` Erişim düzeyini [özel](private.md) veya [korumalı](protected.md)olarak değiştirirseniz, hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="8decd-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="8decd-111">'PointTest.y' koruma düzeyi nedeniyle erişilemez.</span><span class="sxs-lookup"><span data-stu-id="8decd-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8decd-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8decd-112">C# language specification</span></span>  

<span data-ttu-id="8decd-113">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın.</span><span class="sxs-lookup"><span data-stu-id="8decd-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8decd-114">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="8decd-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8decd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8decd-115">See also</span></span>

- [<span data-ttu-id="8decd-116">C# Referans</span><span class="sxs-lookup"><span data-stu-id="8decd-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8decd-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8decd-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8decd-118">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="8decd-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="8decd-119">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="8decd-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8decd-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="8decd-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="8decd-121">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="8decd-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="8decd-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="8decd-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8decd-123">Özel</span><span class="sxs-lookup"><span data-stu-id="8decd-123">private</span></span>](private.md)
- [<span data-ttu-id="8decd-124">protected</span><span class="sxs-lookup"><span data-stu-id="8decd-124">protected</span></span>](protected.md)
- [<span data-ttu-id="8decd-125">Iç</span><span class="sxs-lookup"><span data-stu-id="8decd-125">internal</span></span>](internal.md)
