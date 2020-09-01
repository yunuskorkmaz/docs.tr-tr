---
description: Public anahtar sözcüğü-C# başvurusu
title: Public anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 26edaf7538d11d082a4b8863228213c3ebc46937
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122348"
---
# <a name="public-c-reference"></a><span data-ttu-id="4835a-103">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4835a-103">public (C# Reference)</span></span>

<span data-ttu-id="4835a-104">`public`Anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="4835a-104">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="4835a-105">Genel erişim en çok izin veren erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="4835a-105">Public access is the most permissive access level.</span></span> <span data-ttu-id="4835a-106">Şu örnekte olduğu gibi genel üyelere erişim konusunda kısıtlama yoktur:</span><span class="sxs-lookup"><span data-stu-id="4835a-106">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="4835a-107">Daha fazla bilgi için bkz. [erişim değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md) ve [Erişilebilirlik düzeyleri](accessibility-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="4835a-107">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="4835a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4835a-108">Example</span></span>

<span data-ttu-id="4835a-109">Aşağıdaki örnekte, iki sınıf bildirilmiştir `PointTest` ve `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="4835a-109">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="4835a-110">Ortak üyelerine `x` ve ' `y` a `PointTest` doğrudan üzerinden erişilir `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="4835a-110">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="4835a-111">`public`Erişim düzeyini [özel](private.md) veya [korumalı](protected.md)olarak değiştirirseniz şu hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="4835a-111">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="4835a-112">' PointTest. y ', koruma düzeyi nedeniyle erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="4835a-112">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4835a-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4835a-113">C# language specification</span></span>  

<span data-ttu-id="4835a-114">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="4835a-114">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="4835a-115">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="4835a-115">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="4835a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4835a-116">See also</span></span>

- [<span data-ttu-id="4835a-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4835a-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4835a-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4835a-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4835a-119">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="4835a-119">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="4835a-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4835a-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4835a-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="4835a-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="4835a-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="4835a-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="4835a-123">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="4835a-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="4835a-124">private</span><span class="sxs-lookup"><span data-stu-id="4835a-124">private</span></span>](private.md)
- [<span data-ttu-id="4835a-125">protected</span><span class="sxs-lookup"><span data-stu-id="4835a-125">protected</span></span>](protected.md)
- [<span data-ttu-id="4835a-126">internal</span><span class="sxs-lookup"><span data-stu-id="4835a-126">internal</span></span>](internal.md)
