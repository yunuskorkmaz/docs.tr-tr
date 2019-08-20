---
title: private anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602015"
---
# <a name="private-c-reference"></a><span data-ttu-id="a5acf-102">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a5acf-102">private (C# Reference)</span></span>

<span data-ttu-id="a5acf-103">`private` Anahtar sözcüğü bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="a5acf-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="a5acf-104">Bu sayfa erişimi `private` içerir.</span><span class="sxs-lookup"><span data-stu-id="a5acf-104">This page covers `private` access.</span></span> <span data-ttu-id="a5acf-105">Anahtar sözcüğü ayrıca [`private protected`](./private-protected.md) erişim değiştiricisinin bir parçasıdır. `private`</span><span class="sxs-lookup"><span data-stu-id="a5acf-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="a5acf-106">Özel erişim en az izin veren erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="a5acf-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="a5acf-107">Özel üyelere, bu örnekte olduğu gibi, yalnızca sınıfın gövdesinde veya bildirildiği yapı içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="a5acf-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="a5acf-108">Aynı gövdedeki iç içe türler Ayrıca bu özel üyelere de erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a5acf-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="a5acf-109">Bu, sınıf veya bildirildiği yapı dışında özel bir üyeye başvuruda bulunmak için derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="a5acf-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="a5acf-110">Diğer erişim değiştiricilerine `private` kıyasla, bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a5acf-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5acf-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5acf-111">Example</span></span>

<span data-ttu-id="a5acf-112">Bu örnekte, `Employee` sınıfı iki özel veri `name` üyesi içerir ve `salary`.</span><span class="sxs-lookup"><span data-stu-id="a5acf-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="a5acf-113">Özel Üyeler olarak, üye yöntemleri dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="a5acf-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="a5acf-114">`GetName` Ve`Salary` adlı ortak Yöntemler, Özel üyelere denetimli erişime izin verecek şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="a5acf-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="a5acf-115">Üyeye ortak bir yöntem tarafından erişilir `salary` ve üyeye ortak bir salt okunurdur özelliği tarafından erişilir. `name`</span><span class="sxs-lookup"><span data-stu-id="a5acf-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="a5acf-116">(Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) .)</span><span class="sxs-lookup"><span data-stu-id="a5acf-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="a5acf-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a5acf-117">C# language specification</span></span>  

<span data-ttu-id="a5acf-118">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="a5acf-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="a5acf-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="a5acf-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5acf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5acf-120">See also</span></span>

- [<span data-ttu-id="a5acf-121">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="a5acf-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a5acf-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5acf-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a5acf-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a5acf-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a5acf-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="a5acf-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a5acf-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a5acf-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a5acf-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a5acf-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="a5acf-127">public</span><span class="sxs-lookup"><span data-stu-id="a5acf-127">public</span></span>](public.md)
- [<span data-ttu-id="a5acf-128">protected</span><span class="sxs-lookup"><span data-stu-id="a5acf-128">protected</span></span>](protected.md)
- [<span data-ttu-id="a5acf-129">internal</span><span class="sxs-lookup"><span data-stu-id="a5acf-129">internal</span></span>](internal.md)
