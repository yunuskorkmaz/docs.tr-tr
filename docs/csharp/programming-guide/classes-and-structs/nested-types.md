---
title: İç içe türler-C# Programlama Kılavuzu
description: Bir sınıf, yapı veya arabirim içinde tanımlanan bir türe C# içinde iç içe geçmiş tür denir.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 853138beed6ad9ddffa789f0080ca1fd2ba9d700
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511924"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="cd82d-103">İç içe Geçmiş Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cd82d-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="cd82d-104">Bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) içinde tanımlanan bir türe iç içe geçmiş tür denir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="cd82d-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cd82d-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="cd82d-106">Dış türün bir sınıf, arabirim veya yapı olmasından bağımsız olarak, iç içe geçmiş türler varsayılan olarak [özeldir](../../language-reference/keywords/private.md); bunlara yalnızca kendi içerilen türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="cd82d-107">Önceki örnekte, `Nested` sınıfına dış türler erişilemez.</span><span class="sxs-lookup"><span data-stu-id="cd82d-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="cd82d-108">Ayrıca, iç içe geçmiş bir türün erişilebilirliğini tanımlamak için aşağıdaki gibi bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cd82d-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="cd82d-109">Bir **sınıfın** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md), [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="cd82d-110">Ancak, korumalı bir `protected` `protected internal` `private protected` [sınıf](../../language-reference/keywords/sealed.md) içinde veya iç içe yerleştirilmiş bir sınıf tanımlamak, "korumalı sınıfta belirtilen yeni korunan üye" Derleyici Uyarısı [CS0628](../../misc/cs0628.md)oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd82d-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>

   <span data-ttu-id="cd82d-111">Ayrıca, iç içe bir türün dışarıdan görünür hale getirilmesi, kod kalitesi kuralı [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) "iç içe geçmiş türleri görünür olmamalıdır" olarak ihlal ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cd82d-111">Also be aware that making a nested type externally visible violates the code quality rule [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) "Nested types should not be visible".</span></span>

- <span data-ttu-id="cd82d-112">Bir **yapının** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-112">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="cd82d-113">Aşağıdaki örnek, `Nested` sınıfı genel yapar:</span><span class="sxs-lookup"><span data-stu-id="cd82d-113">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="cd82d-114">İç içe geçmiş veya iç, türü kapsayan veya OUTER öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-114">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="cd82d-115">Kapsayan türe erişmek için, onu iç içe geçmiş türün oluşturucusuna bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="cd82d-115">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="cd82d-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="cd82d-116">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="cd82d-117">İç içe bir tür, kapsayan türü tarafından erişilebilen tüm üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-117">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="cd82d-118">Devralınan korunan üyeler de dahil olmak üzere, kapsayan türün özel ve korumalı üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cd82d-118">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="cd82d-119">Önceki bildirimde, sınıfının tam adı `Nested` `Container.Nested` .</span><span class="sxs-lookup"><span data-stu-id="cd82d-119">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="cd82d-120">Bu, aşağıdaki gibi, iç içe yerleştirilmiş sınıfın yeni bir örneğini oluşturmak için kullanılan addır:</span><span class="sxs-lookup"><span data-stu-id="cd82d-120">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="cd82d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd82d-121">See also</span></span>

- [<span data-ttu-id="cd82d-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cd82d-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd82d-123">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="cd82d-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="cd82d-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="cd82d-124">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="cd82d-125">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="cd82d-125">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="cd82d-126">CA1034 kuralı</span><span class="sxs-lookup"><span data-stu-id="cd82d-126">CA1034 rule</span></span>](../../../fundamentals/code-analysis/quality-rules/ca1034.md)
