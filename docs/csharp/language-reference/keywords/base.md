---
title: Base anahtar sözcüğü C# -başvurusu
ms.custom: seodec18
description: İçindeki C#türetilmiş bir sınıftan temel sınıfın üyelerine erişmek için kullanılan temel anahtar sözcüğü hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: b882a8d1e5979ac184d184be379dd76f7bf3600f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602262"
---
# <a name="base-c-reference"></a><span data-ttu-id="6cf46-103">base (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6cf46-103">base (C# Reference)</span></span>

<span data-ttu-id="6cf46-104">`base` Anahtar sözcüğü türetilmiş bir sınıf içinden temel sınıfın üyelerine erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6cf46-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="6cf46-105">Temel sınıfta, başka bir yöntem tarafından geçersiz kılınan bir yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="6cf46-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="6cf46-106">Türetilmiş sınıfın örneklerini oluştururken hangi temel sınıf oluşturucunun çağrılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="6cf46-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="6cf46-107">Temel sınıf erişimine yalnızca bir oluşturucuda, örnek yönteminde veya örnek özellik erişimcisinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6cf46-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="6cf46-108">`base` Anahtar sözcüğünün statik bir yöntem içinden kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="6cf46-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="6cf46-109">Erişilen temel sınıf, sınıf bildiriminde belirtilen temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="6cf46-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="6cf46-110">Örneğin, öğesini belirtirseniz `class ClassB : ClassA`, ClassA 'nın temel sınıfından bağımsız olarak SınıfB ' den erişim altına alınır.</span><span class="sxs-lookup"><span data-stu-id="6cf46-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="6cf46-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cf46-111">Example</span></span>

<span data-ttu-id="6cf46-112">Bu örnekte, hem taban sınıfının `Person`hem de türetilmiş `Employee`sınıfın adında `Getinfo`bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="6cf46-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="6cf46-113">`base` Anahtar sözcüğünü kullanarak, türetilmiş sınıfın içindeki `Getinfo` yöntemi temel sınıfta çağırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6cf46-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="6cf46-114">Daha fazla örnek için bkz. [New](new-modifier.md), [Virtual](virtual.md)ve [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="6cf46-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="6cf46-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cf46-115">Example</span></span>

<span data-ttu-id="6cf46-116">Bu örnek, türetilmiş bir sınıfın örneklerini oluştururken çağrılan temel sınıf oluşturucunun nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cf46-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="6cf46-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6cf46-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6cf46-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cf46-118">See also</span></span>

- [<span data-ttu-id="6cf46-119">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6cf46-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6cf46-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6cf46-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6cf46-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6cf46-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="6cf46-122">this</span><span class="sxs-lookup"><span data-stu-id="6cf46-122">this</span></span>](./this.md)
