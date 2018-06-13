---
title: base (C# Başvurusu)
description: Temel sınıfından türetilen bir sınıfta C# içinde üyelerine erişmek için kullanılan temel anahtar hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 69885ba0b2d05c79f2b7ba9458e7ba8c8b7aa0c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214487"
---
# <a name="base-c-reference"></a><span data-ttu-id="d0559-103">base (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d0559-103">base (C# Reference)</span></span>

<span data-ttu-id="d0559-104">`base` Anahtar sözcüğü temel sınıfından türetilmiş bir sınıf içinde üyelerine erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d0559-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="d0559-105">Başka bir yöntem tarafından geçersiz kılınmış temel sınıfı üzerinde bir yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d0559-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="d0559-106">Hangi temel sınıf oluşturucu, türetilmiş sınıf örnekleri oluşturulurken çağrılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="d0559-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="d0559-107">Bir temel sınıf erişim, yalnızca bir oluşturucu, örnek yöntemi veya bir örnek özelliği erişimcisi izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d0559-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="d0559-108">Kullanmak için bir hata olduğunu `base` anahtar sözcüğü bir statik yöntem içinde.</span><span class="sxs-lookup"><span data-stu-id="d0559-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="d0559-109">Erişilen temel sınıf sınıfı bildiriminde belirtilen temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d0559-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="d0559-110">Örneğin, belirtirseniz `class ClassB : ClassA`, ClassA temel sınıfını bakılmaksızın ClassB erişilen ClassA üyeleri.</span><span class="sxs-lookup"><span data-stu-id="d0559-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="d0559-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0559-111">Example</span></span>
<span data-ttu-id="d0559-112">Bu örnekte, iki temel sınıfı olan `Person`ve türetilmiş sınıf `Employee`, adlandırılmış bir yöntemine sahip `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="d0559-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="d0559-113">Kullanarak `base` anahtar sözcüğü, onu çağırmak olası `Getinfo` içinden temel sınıf yöntemi türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="d0559-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

<span data-ttu-id="d0559-114">Ek örnekler için bkz: [yeni](../../../csharp/language-reference/keywords/new.md), [sanal](../../../csharp/language-reference/keywords/virtual.md), ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="d0559-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="d0559-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0559-115">Example</span></span>
<span data-ttu-id="d0559-116">Bu örnek, türetilmiş bir sınıf örnekleri oluşturulurken adlı temel sınıf oluşturucu belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d0559-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="d0559-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d0559-117">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d0559-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0559-118">See also</span></span>
 [<span data-ttu-id="d0559-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d0559-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d0559-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d0559-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d0559-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d0559-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d0559-122">this</span><span class="sxs-lookup"><span data-stu-id="d0559-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)