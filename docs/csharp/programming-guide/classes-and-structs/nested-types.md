---
title: İç içe türler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 7269f925b3fc78eea04249984697899b1997c3fb
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976713"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="f6436-102">İç içe Geçmiş Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f6436-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="f6436-103">İçinde tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) iç içe geçmiş bir tür olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f6436-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="f6436-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f6436-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
<span data-ttu-id="f6436-105">Dış türün bir sınıf veya yapı olup olmadığına bakılmaksızın, iç içe geçmiş türler varsayılan olarak [özel](../../../csharp/language-reference/keywords/private.md); yalnızca kendi kapsayan türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f6436-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="f6436-106">Önceki örnekte, `Nested` sınıfı, dış türler için erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="f6436-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="f6436-107">Ayrıca belirtebileceğiniz bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) gibi iç içe türün erişilebilirliği tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f6436-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="f6436-108">İç içe türleri bir **sınıfı** olabilir [genel](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md), [özel](../../../csharp/language-reference/keywords/private.md) veya [korunan özel](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="f6436-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="f6436-109">Ancak, tanımlama bir `protected`, `protected internal` veya `private protected` sınıf içinde iç içe geçmiş bir [sınıfı korumalı](../../language-reference/keywords/sealed.md) derleyici uyarısı oluşturur [CS0628](../../misc/cs0628.md), "Yeni korunan üye korumalı sınıfta belirtildi."</span><span class="sxs-lookup"><span data-stu-id="f6436-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="f6436-110">İç içe türleri bir **yapı** olabilir [genel](../../../csharp/language-reference/keywords/public.md), [iç](../../../csharp/language-reference/keywords/internal.md), veya [özel](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="f6436-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="f6436-111">Aşağıdaki örnekte `Nested` sınıfı genel:</span><span class="sxs-lookup"><span data-stu-id="f6436-111">The following example makes the `Nested` class public:</span></span>
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 <span data-ttu-id="f6436-112">İç içe geçmiş ya da iç, tür, kapsayıcı veya dış türe erişim sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f6436-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="f6436-113">Kapsayan türe erişmek için bir bağımsız değişken olarak iç içe türün oluşturucuya geçirin.</span><span class="sxs-lookup"><span data-stu-id="f6436-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="f6436-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f6436-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 <span data-ttu-id="f6436-115">İç içe türü, kapsadığı tür için erişilebilir olan üyelerin tümüne erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f6436-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="f6436-116">Bu devralınan tüm korumalı Üyeler dahil olmak üzere kapsanan türün özel ve korumalı üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f6436-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="f6436-117">Önceki bildirimde, sınıfın tam adını `Nested` olduğu `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="f6436-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="f6436-118">Bu gibi iç içe geçmiş sınıfın yeni bir örneğini oluşturmak için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="f6436-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a><span data-ttu-id="f6436-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6436-119">See also</span></span>

- [<span data-ttu-id="f6436-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f6436-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f6436-121">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="f6436-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="f6436-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="f6436-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="f6436-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f6436-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
