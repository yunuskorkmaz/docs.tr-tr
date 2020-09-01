---
description: private anahtar sözcüğü-C# başvurusu
title: private anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139404"
---
# <a name="private-c-reference"></a><span data-ttu-id="0b398-103">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0b398-103">private (C# Reference)</span></span>

<span data-ttu-id="0b398-104">`private`Anahtar sözcüğü bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="0b398-104">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="0b398-105">Bu sayfa `private` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="0b398-105">This page covers `private` access.</span></span> <span data-ttu-id="0b398-106">`private`Anahtar sözcüğü ayrıca [`private protected`](./private-protected.md) erişim değiştiricisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0b398-106">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="0b398-107">Özel erişim en az izin veren erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="0b398-107">Private access is the least permissive access level.</span></span> <span data-ttu-id="0b398-108">Özel üyelere, bu örnekte olduğu gibi, yalnızca sınıfın gövdesinde veya bildirildiği yapı içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="0b398-108">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="0b398-109">Aynı gövdedeki iç içe türler Ayrıca bu özel üyelere de erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0b398-109">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="0b398-110">Bu, sınıf veya bildirildiği yapı dışında özel bir üyeye başvuruda bulunmak için derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="0b398-110">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="0b398-111">`private`Diğer erişim değiştiricilerine kıyasla, bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0b398-111">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="0b398-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b398-112">Example</span></span>

<span data-ttu-id="0b398-113">Bu örnekte, `Employee` sınıfı iki özel veri üyesi içerir `name` ve `salary` .</span><span class="sxs-lookup"><span data-stu-id="0b398-113">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="0b398-114">Özel Üyeler olarak, üye yöntemleri dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="0b398-114">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="0b398-115">Ve adlı ortak `GetName` Yöntemler `Salary` , Özel üyelere denetimli erişime izin verecek şekilde eklenir.</span><span class="sxs-lookup"><span data-stu-id="0b398-115">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="0b398-116">`name`Üyeye ortak bir yöntem tarafından erişilir ve `salary` üyeye ortak bir salt okunurdur özelliği tarafından erişilir.</span><span class="sxs-lookup"><span data-stu-id="0b398-116">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="0b398-117">(Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) .)</span><span class="sxs-lookup"><span data-stu-id="0b398-117">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="0b398-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0b398-118">C# language specification</span></span>  

<span data-ttu-id="0b398-119">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="0b398-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0b398-120">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0b398-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b398-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b398-121">See also</span></span>

- [<span data-ttu-id="0b398-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0b398-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0b398-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b398-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0b398-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0b398-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0b398-125">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="0b398-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="0b398-126">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0b398-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="0b398-127">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="0b398-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="0b398-128">genel</span><span class="sxs-lookup"><span data-stu-id="0b398-128">public</span></span>](public.md)
- [<span data-ttu-id="0b398-129">protected</span><span class="sxs-lookup"><span data-stu-id="0b398-129">protected</span></span>](protected.md)
- [<span data-ttu-id="0b398-130">internal</span><span class="sxs-lookup"><span data-stu-id="0b398-130">internal</span></span>](internal.md)
