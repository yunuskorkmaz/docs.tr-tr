---
title: private anahtar sözcüğü C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715193"
---
# <a name="private-c-reference"></a><span data-ttu-id="56b52-102">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="56b52-102">private (C# Reference)</span></span>

<span data-ttu-id="56b52-103">`private` anahtar sözcüğü bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="56b52-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="56b52-104">Bu sayfa `private` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="56b52-104">This page covers `private` access.</span></span> <span data-ttu-id="56b52-105">`private` anahtar sözcüğü ayrıca [`private protected`](./private-protected.md) erişim değiştiricisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="56b52-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="56b52-106">Özel erişim en az izin veren erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="56b52-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="56b52-107">Özel üyelere, bu örnekte olduğu gibi, yalnızca sınıfın gövdesinde veya bildirildiği yapı içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="56b52-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="56b52-108">Aynı gövdedeki iç içe türler Ayrıca bu özel üyelere de erişebilir.</span><span class="sxs-lookup"><span data-stu-id="56b52-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="56b52-109">Bu, sınıf veya bildirildiği yapı dışında özel bir üyeye başvuruda bulunmak için derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="56b52-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="56b52-110">Diğer erişim değiştiricilerine sahip `private` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="56b52-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="56b52-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="56b52-111">Example</span></span>

<span data-ttu-id="56b52-112">Bu örnekte, `Employee` sınıfı iki özel veri üyesi içerir, `name` ve `salary`.</span><span class="sxs-lookup"><span data-stu-id="56b52-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="56b52-113">Özel Üyeler olarak, üye yöntemleri dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="56b52-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="56b52-114">`GetName` ve `Salary` adlı ortak Yöntemler, Özel üyelere denetimli erişime izin verecek şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="56b52-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="56b52-115">`name` üyesine ortak bir yöntem yoluyla erişilir ve `salary` üyesine ortak bir salt okunurdur özelliği tarafından erişilir.</span><span class="sxs-lookup"><span data-stu-id="56b52-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="56b52-116">(Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) .)</span><span class="sxs-lookup"><span data-stu-id="56b52-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="56b52-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="56b52-117">C# language specification</span></span>  

<span data-ttu-id="56b52-118">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="56b52-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="56b52-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="56b52-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="56b52-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56b52-120">See also</span></span>

- [<span data-ttu-id="56b52-121">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="56b52-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="56b52-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="56b52-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="56b52-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="56b52-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="56b52-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="56b52-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="56b52-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="56b52-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="56b52-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="56b52-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="56b52-127">public</span><span class="sxs-lookup"><span data-stu-id="56b52-127">public</span></span>](public.md)
- [<span data-ttu-id="56b52-128">protected</span><span class="sxs-lookup"><span data-stu-id="56b52-128">protected</span></span>](protected.md)
- [<span data-ttu-id="56b52-129">internal</span><span class="sxs-lookup"><span data-stu-id="56b52-129">internal</span></span>](internal.md)
