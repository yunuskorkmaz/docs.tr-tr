---
title: özel anahtar kelime - C# Reference
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715193"
---
# <a name="private-c-reference"></a><span data-ttu-id="47bc9-102">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="47bc9-102">private (C# Reference)</span></span>

<span data-ttu-id="47bc9-103">Anahtar `private` kelime bir üye erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="47bc9-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="47bc9-104">Bu sayfa `private` erişimi kapsar.</span><span class="sxs-lookup"><span data-stu-id="47bc9-104">This page covers `private` access.</span></span> <span data-ttu-id="47bc9-105">Anahtar `private` kelime de erişim [`private protected`](./private-protected.md) değiştiricinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="47bc9-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="47bc9-106">Özel erişim en az izin verilen erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="47bc9-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="47bc9-107">Özel üyelere, bu örnekte olduğu gibi, yalnızca sınıfın gövdesi nde veya beyan edildikleri yapı içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="47bc9-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="47bc9-108">Aynı gövdedeki iç içe geçen türler de bu özel üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="47bc9-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="47bc9-109">Sınıf veya beyan edildiği yapı dışında özel bir üyeye başvurmak için bir derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="47bc9-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="47bc9-110">Diğer erişim `private` değiştiriciler ile karşılaştırma [için, Erişilebilirlik Düzeyleri](accessibility-levels.md) ve [Erişim Değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="47bc9-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="47bc9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="47bc9-111">Example</span></span>

<span data-ttu-id="47bc9-112">Bu örnekte, `Employee` sınıf iki özel `name` veri `salary`üyesi içerir ve .</span><span class="sxs-lookup"><span data-stu-id="47bc9-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="47bc9-113">Özel üyeler olarak, üye yöntemleri dışında erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="47bc9-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="47bc9-114">Özel üyelere kontrollü erişim sağlamak için adlandırılmış `GetName` ve `Salary` eklenen genel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="47bc9-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="47bc9-115">Üyeye `name` genel bir yöntemle erişilir ve `salary` üyeye herkese açık salt okunur bir özellik ile erişilir.</span><span class="sxs-lookup"><span data-stu-id="47bc9-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="47bc9-116">(Daha fazla bilgi için [Özellikler'e](../../programming-guide/classes-and-structs/properties.md) bakın.)</span><span class="sxs-lookup"><span data-stu-id="47bc9-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="47bc9-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="47bc9-117">C# language specification</span></span>  

<span data-ttu-id="47bc9-118">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın.</span><span class="sxs-lookup"><span data-stu-id="47bc9-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="47bc9-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="47bc9-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="47bc9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47bc9-120">See also</span></span>

- [<span data-ttu-id="47bc9-121">C# Referans</span><span class="sxs-lookup"><span data-stu-id="47bc9-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47bc9-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="47bc9-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47bc9-123">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="47bc9-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="47bc9-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="47bc9-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="47bc9-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="47bc9-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="47bc9-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="47bc9-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="47bc9-127">Kamu</span><span class="sxs-lookup"><span data-stu-id="47bc9-127">public</span></span>](public.md)
- [<span data-ttu-id="47bc9-128">protected</span><span class="sxs-lookup"><span data-stu-id="47bc9-128">protected</span></span>](protected.md)
- [<span data-ttu-id="47bc9-129">Iç</span><span class="sxs-lookup"><span data-stu-id="47bc9-129">internal</span></span>](internal.md)
