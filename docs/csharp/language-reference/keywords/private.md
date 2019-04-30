---
title: private anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 62a78649a96d0a1b03758508241395d7f061504b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660911"
---
# <a name="private-c-reference"></a><span data-ttu-id="0c63d-102">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0c63d-102">private (C# Reference)</span></span>

<span data-ttu-id="0c63d-103">`private` Anahtar sözcüğü, bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0c63d-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="0c63d-104">Bu sayfa kapsayan `private` erişim.</span><span class="sxs-lookup"><span data-stu-id="0c63d-104">This page covers `private` access.</span></span> <span data-ttu-id="0c63d-105">`private` Anahtar sözcüğü, ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0c63d-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="0c63d-106">Özel erişim en katı erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="0c63d-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="0c63d-107">Özel üyeler, yalnızca sınıf veya yapı içinde bu örnekte olduğu gibi bildirildikleri gövdesi içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="0c63d-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="0c63d-108">İç içe geçmiş türler aynı gövdesinde, bu özel üyeler de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c63d-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="0c63d-109">Bu sınıf veya yapı birimi içinde bildirildiği dışındaki özel üye başvurmak için bir derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="0c63d-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="0c63d-110">Bir karşılaştırması `private` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0c63d-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c63d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c63d-111">Example</span></span>

<span data-ttu-id="0c63d-112">Bu örnekte, `Employee` sınıfı içeren iki özel veri üyeleri, `name` ve `salary`.</span><span class="sxs-lookup"><span data-stu-id="0c63d-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="0c63d-113">Özel üyeler bunlar dışında üye yöntemleri tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="0c63d-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="0c63d-114">Genel yöntemler adlı `GetName` ve `Salary` özel üyeler denetimli erişim izni vermek için eklenir.</span><span class="sxs-lookup"><span data-stu-id="0c63d-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="0c63d-115">`name` Genel bir yöntem aracılığıyla erişilen üyenin ve `salary` genel bir salt okunur özelliği yoluyla erişilen üyenin.</span><span class="sxs-lookup"><span data-stu-id="0c63d-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="0c63d-116">(Bkz [özellikleri](../../programming-guide/classes-and-structs/properties.md) daha fazla bilgi için.)</span><span class="sxs-lookup"><span data-stu-id="0c63d-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="0c63d-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0c63d-117">C# language specification</span></span>  

<span data-ttu-id="0c63d-118">Daha fazla bilgi için [erişilebilirlik bildirilen](~/_csharplang/spec/basic-concepts.md#declared-accessibility) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c63d-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="0c63d-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0c63d-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c63d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c63d-120">See also</span></span>

- [<span data-ttu-id="0c63d-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0c63d-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="0c63d-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0c63d-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0c63d-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0c63d-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0c63d-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="0c63d-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="0c63d-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0c63d-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="0c63d-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="0c63d-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="0c63d-127">public</span><span class="sxs-lookup"><span data-stu-id="0c63d-127">public</span></span>](public.md)
- [<span data-ttu-id="0c63d-128">protected</span><span class="sxs-lookup"><span data-stu-id="0c63d-128">protected</span></span>](protected.md)
- [<span data-ttu-id="0c63d-129">internal</span><span class="sxs-lookup"><span data-stu-id="0c63d-129">internal</span></span>](internal.md)