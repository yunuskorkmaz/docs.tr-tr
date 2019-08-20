---
title: İç içe türler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: de2e369702c48047835bc49b98df8f48fbd13480
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596528"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="27f3c-102">İç içe Geçmiş Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="27f3c-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="27f3c-103">Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) içinde tanımlanan bir türe iç içe geçmiş tür denir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-103">A type defined within a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="27f3c-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27f3c-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
<span data-ttu-id="27f3c-105">Dış türün bir sınıf veya yapı olmasından bağımsız olarak, iç içe geçmiş türler varsayılan olarak [özeldir](../../language-reference/keywords/private.md); bunlara yalnızca kendi içerilen türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="27f3c-106">Önceki örnekte, `Nested` sınıfına dış türler erişilemez.</span><span class="sxs-lookup"><span data-stu-id="27f3c-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="27f3c-107">Ayrıca, iç içe geçmiş bir türün erişilebilirliğini tanımlamak için aşağıdaki gibi bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27f3c-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="27f3c-108">Bir **sınıfın** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md), [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="27f3c-109">Ancak, korumalı bir `protected` [sınıf](../../language-reference/keywords/sealed.md) içinde `private protected` `protected internal` veya iç içe yerleştirilmiş bir sınıf tanımlamak, "korumalı sınıfta belirtilen yeni korunan üye" Derleyici Uyarısı [CS0628](../../misc/cs0628.md)oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27f3c-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="27f3c-110">Bir **yapının** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="27f3c-111">Aşağıdaki örnek, `Nested` sınıfı genel yapar:</span><span class="sxs-lookup"><span data-stu-id="27f3c-111">The following example makes the `Nested` class public:</span></span>
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 <span data-ttu-id="27f3c-112">İç içe geçmiş veya iç, türü kapsayan veya OUTER öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="27f3c-113">Kapsayan türe erişmek için, onu iç içe geçmiş türün oluşturucusuna bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="27f3c-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="27f3c-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27f3c-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 <span data-ttu-id="27f3c-115">İç içe bir tür, kapsayan türü tarafından erişilebilen tüm üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="27f3c-116">Devralınan korunan üyeler de dahil olmak üzere, kapsayan türün özel ve korumalı üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="27f3c-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="27f3c-117">Önceki bildirimde, sınıfının `Nested` `Container.Nested`tam adı.</span><span class="sxs-lookup"><span data-stu-id="27f3c-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="27f3c-118">Bu, aşağıdaki gibi, iç içe yerleştirilmiş sınıfın yeni bir örneğini oluşturmak için kullanılan addır:</span><span class="sxs-lookup"><span data-stu-id="27f3c-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a><span data-ttu-id="27f3c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27f3c-119">See also</span></span>

- [<span data-ttu-id="27f3c-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="27f3c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="27f3c-121">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="27f3c-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="27f3c-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="27f3c-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="27f3c-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="27f3c-123">Constructors</span></span>](./constructors.md)
