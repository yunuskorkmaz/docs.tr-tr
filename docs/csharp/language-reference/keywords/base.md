---
title: temel anahtar kelime - C# Başvuru
description: C#'da türetilmiş bir sınıfın içinden taban sınıfın üyelerine erişmek için kullanılan temel anahtar kelime hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713763"
---
# <a name="base-c-reference"></a><span data-ttu-id="770a1-103">base (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="770a1-103">base (C# Reference)</span></span>

<span data-ttu-id="770a1-104">Anahtar `base` kelime, türemiş bir sınıfın içinden taban sınıfın üyelerine erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="770a1-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="770a1-105">Taban sınıfta başka bir yöntem tarafından geçersiz kılınan bir yöntem çağırın.</span><span class="sxs-lookup"><span data-stu-id="770a1-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="770a1-106">Türemiş sınıfın örneklerini oluştururken hangi taban sınıf oluşturucunun çağrılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="770a1-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="770a1-107">Taban sınıf erişimine yalnızca bir oluşturucu, örnek yöntemi veya örnek özellik erişimcisi olarak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="770a1-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="770a1-108">Bu statik bir yöntem `base` içinde anahtar kelime kullanmak için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="770a1-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="770a1-109">Erişilen taban sınıf, sınıf bildiriminde belirtilen taban sınıftır.</span><span class="sxs-lookup"><span data-stu-id="770a1-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="770a1-110">Örneğin, SınıfA'nın taban sınıfından bağımsız olarak, ClassA üyelerine B sınıfından erişilir. `class ClassB : ClassA`</span><span class="sxs-lookup"><span data-stu-id="770a1-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="770a1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="770a1-111">Example</span></span>

<span data-ttu-id="770a1-112">Bu örnekte, hem taban `Person`sınıf, hem `Employee`de türemiş `Getinfo`sınıf, adlı bir yöntem var.</span><span class="sxs-lookup"><span data-stu-id="770a1-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="770a1-113">`base` Anahtar sözcüğü kullanarak, türemiş `Getinfo` sınıf içinden, taban sınıfta yöntemi aramak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="770a1-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="770a1-114">Ek örnekler için, [bkz. yeni](new-modifier.md), [sanal](virtual.md), ve [geçersiz kılma.](override.md)</span><span class="sxs-lookup"><span data-stu-id="770a1-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="770a1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="770a1-115">Example</span></span>

<span data-ttu-id="770a1-116">Bu örnek, türemiş bir sınıfın örneklerini oluştururken çağrılan taban sınıf oluşturucunun nasıl belirtileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="770a1-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="770a1-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="770a1-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="770a1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="770a1-118">See also</span></span>

- [<span data-ttu-id="770a1-119">C# Referans</span><span class="sxs-lookup"><span data-stu-id="770a1-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="770a1-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="770a1-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="770a1-121">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="770a1-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="770a1-122">bu</span><span class="sxs-lookup"><span data-stu-id="770a1-122">this</span></span>](./this.md)
