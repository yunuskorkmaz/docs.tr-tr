---
title: İç içe türler-C# Programlama Kılavuzu
description: Bir sınıf, yapı veya arabirim içinde tanımlanan bir türe C# içinde iç içe geçmiş tür denir.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864949"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="7a855-103">İç içe Geçmiş Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7a855-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="7a855-104">Bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) içinde tanımlanan bir türe iç içe geçmiş tür denir.</span><span class="sxs-lookup"><span data-stu-id="7a855-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="7a855-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7a855-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="7a855-106">Dış türün bir sınıf, arabirim veya yapı olmasından bağımsız olarak, iç içe geçmiş türler varsayılan olarak [özeldir](../../language-reference/keywords/private.md); bunlara yalnızca kendi içerilen türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a855-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="7a855-107">Önceki örnekte, `Nested` sınıfına dış türler erişilemez.</span><span class="sxs-lookup"><span data-stu-id="7a855-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="7a855-108">Ayrıca, iç içe geçmiş bir türün erişilebilirliğini tanımlamak için aşağıdaki gibi bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7a855-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="7a855-109">Bir **sınıfın** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md), [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a855-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="7a855-110">Ancak, korumalı bir `protected` `protected internal` `private protected` [sınıf](../../language-reference/keywords/sealed.md) içinde veya iç içe yerleştirilmiş bir sınıf tanımlamak, "korumalı sınıfta belirtilen yeni korunan üye" Derleyici Uyarısı [CS0628](../../misc/cs0628.md)oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a855-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="7a855-111">Bir **yapının** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a855-111">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="7a855-112">Aşağıdaki örnek, `Nested` sınıfı genel yapar:</span><span class="sxs-lookup"><span data-stu-id="7a855-112">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="7a855-113">İç içe geçmiş veya iç, türü kapsayan veya OUTER öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7a855-113">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="7a855-114">Kapsayan türe erişmek için, onu iç içe geçmiş türün oluşturucusuna bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="7a855-114">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="7a855-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7a855-115">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="7a855-116">İç içe bir tür, kapsayan türü tarafından erişilebilen tüm üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7a855-116">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="7a855-117">Devralınan korunan üyeler de dahil olmak üzere, kapsayan türün özel ve korumalı üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7a855-117">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="7a855-118">Önceki bildirimde, sınıfının tam adı `Nested` `Container.Nested` .</span><span class="sxs-lookup"><span data-stu-id="7a855-118">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="7a855-119">Bu, aşağıdaki gibi, iç içe yerleştirilmiş sınıfın yeni bir örneğini oluşturmak için kullanılan addır:</span><span class="sxs-lookup"><span data-stu-id="7a855-119">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="7a855-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a855-120">See also</span></span>

- [<span data-ttu-id="7a855-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a855-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7a855-122">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="7a855-122">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7a855-123">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="7a855-123">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="7a855-124">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7a855-124">Constructors</span></span>](./constructors.md)
