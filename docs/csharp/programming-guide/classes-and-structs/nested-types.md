---
title: İç Içe Türler - C# Programlama Kılavuzu
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626496"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="0014b-102">İç içe Geçmiş Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0014b-102">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="0014b-103">Bir [sınıf](../../language-reference/keywords/class.md)içinde tanımlanan bir tür, [yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) iç içe türü denir.</span><span class="sxs-lookup"><span data-stu-id="0014b-103">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="0014b-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0014b-104">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="0014b-105">Dış türün bir sınıf, arabirim veya yapı olup olmadığına bakılmaksızın, iç içe dönük türler varsayılan [olarak özel;](../../language-reference/keywords/private.md) yalnızca kendi türlerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0014b-105">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="0014b-106">Önceki örnekte, `Nested` sınıf dış türleri için erişilemez.</span><span class="sxs-lookup"><span data-stu-id="0014b-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="0014b-107">İç içe bir türün erişilebilirliğini tanımlamak için bir [erişim değiştirici](../../language-reference/keywords/access-modifiers.md) sini aşağıdaki gibi belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0014b-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="0014b-108">Bir **sınıfın** iç içe geçme türleri [kamu,](../../language-reference/keywords/public.md) [korumalı,](../../language-reference/keywords/protected.md) [iç,](../../language-reference/keywords/internal.md) [korumalı iç,](../../language-reference/keywords/protected-internal.md) [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="0014b-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="0014b-109">Ancak, mühürlü `protected` `protected internal` bir `private protected` [sınıf](../../language-reference/keywords/sealed.md) içinde bir , veya iç içe sınıf tanımlama derleyici uyarı [CS0628](../../misc/cs0628.md)oluşturur , "yeni korumalı üye mühürlü sınıfta ilan."</span><span class="sxs-lookup"><span data-stu-id="0014b-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="0014b-110">Bir **yapının** iç içe geçme türleri [genel,](../../language-reference/keywords/public.md) [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="0014b-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="0014b-111">Aşağıdaki `Nested` örnek, sınıfı herkese açık hale getirir:</span><span class="sxs-lookup"><span data-stu-id="0014b-111">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="0014b-112">İç içe veya iç, türü içeren veya dış, türü erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0014b-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="0014b-113">İçerme türüne erişmek için, iç içe geçen türün oluşturucuya bağımsız değişken olarak aktarın.</span><span class="sxs-lookup"><span data-stu-id="0014b-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="0014b-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0014b-114">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="0014b-115">İç içe bir tür, içerdiği türüne erişilebilen tüm üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0014b-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="0014b-116">Devralınan korumalı üyeler de dahil olmak üzere, ilgili türün özel ve korumalı üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0014b-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="0014b-117">Önceki bildirimde, sınıfın `Nested` tam adı `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="0014b-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="0014b-118">Bu, iç içe geçen sınıfın yeni bir örneğini oluşturmak için kullanılan addır:</span><span class="sxs-lookup"><span data-stu-id="0014b-118">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="0014b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0014b-119">See also</span></span>

- [<span data-ttu-id="0014b-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0014b-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0014b-121">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="0014b-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="0014b-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="0014b-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="0014b-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0014b-123">Constructors</span></span>](./constructors.md)
