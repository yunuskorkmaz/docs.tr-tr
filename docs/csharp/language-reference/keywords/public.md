---
title: ortak anahtar sözcük C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422553"
---
# <a name="public-c-reference"></a><span data-ttu-id="3ee84-102">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3ee84-102">public (C# Reference)</span></span>

<span data-ttu-id="3ee84-103">`public` anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="3ee84-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="3ee84-104">Genel erişim en çok izin veren erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="3ee84-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="3ee84-105">Şu örnekte olduğu gibi genel üyelere erişim konusunda kısıtlama yoktur:</span><span class="sxs-lookup"><span data-stu-id="3ee84-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="3ee84-106">Daha fazla bilgi için bkz. [erişim değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md) ve [Erişilebilirlik düzeyleri](accessibility-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="3ee84-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="3ee84-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ee84-107">Example</span></span>

<span data-ttu-id="3ee84-108">Aşağıdaki örnekte, `PointTest` ve `MainClass`iki sınıf bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ee84-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="3ee84-109">`PointTest` `x` ve `y` ortak üyelere doğrudan `MainClass`erişilir.</span><span class="sxs-lookup"><span data-stu-id="3ee84-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="3ee84-110">`public` erişim düzeyini [özel](private.md) veya [korumalı](protected.md)olarak değiştirirseniz, şu hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="3ee84-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="3ee84-111">' PointTest. y ', koruma düzeyi nedeniyle erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="3ee84-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3ee84-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3ee84-112">C# language specification</span></span>  

<span data-ttu-id="3ee84-113">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="3ee84-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="3ee84-114">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3ee84-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee84-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ee84-115">See also</span></span>

- [<span data-ttu-id="3ee84-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="3ee84-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3ee84-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3ee84-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ee84-118">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="3ee84-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3ee84-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3ee84-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3ee84-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="3ee84-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="3ee84-121">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="3ee84-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="3ee84-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3ee84-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3ee84-123">private</span><span class="sxs-lookup"><span data-stu-id="3ee84-123">private</span></span>](private.md)
- [<span data-ttu-id="3ee84-124">protected</span><span class="sxs-lookup"><span data-stu-id="3ee84-124">protected</span></span>](protected.md)
- [<span data-ttu-id="3ee84-125">internal</span><span class="sxs-lookup"><span data-stu-id="3ee84-125">internal</span></span>](internal.md)
