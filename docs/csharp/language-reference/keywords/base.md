---
title: Base anahtar sözcüğü C# -başvurusu
description: İçindeki C#türetilmiş bir sınıftan temel sınıfın üyelerine erişmek için kullanılan temel anahtar sözcüğü hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713763"
---
# <a name="base-c-reference"></a><span data-ttu-id="618fc-103">base (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="618fc-103">base (C# Reference)</span></span>

<span data-ttu-id="618fc-104">`base` anahtar sözcüğü, türetilmiş bir sınıfın içindeki temel sınıfın üyelerine erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="618fc-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="618fc-105">Temel sınıfta, başka bir yöntem tarafından geçersiz kılınan bir yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="618fc-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="618fc-106">Türetilmiş sınıfın örneklerini oluştururken hangi temel sınıf oluşturucunun çağrılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="618fc-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="618fc-107">Temel sınıf erişimine yalnızca bir oluşturucuda, örnek yönteminde veya örnek özellik erişimcisinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="618fc-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="618fc-108">Statik bir yöntem içinden `base` anahtar sözcüğünü kullanmak hatadır.</span><span class="sxs-lookup"><span data-stu-id="618fc-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="618fc-109">Erişilen temel sınıf, sınıf bildiriminde belirtilen temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="618fc-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="618fc-110">Örneğin, `class ClassB : ClassA`belirtirseniz ClassA 'nın üyelerine, ClassA 'nın temel sınıfına bakılmaksızın ClassB 'den erişilir.</span><span class="sxs-lookup"><span data-stu-id="618fc-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="618fc-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="618fc-111">Example</span></span>

<span data-ttu-id="618fc-112">Bu örnekte, hem temel sınıf, `Person`hem de türetilmiş sınıf `Employee`, `Getinfo`adlı bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="618fc-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="618fc-113">`base` anahtar sözcüğünü kullanarak, türetilmiş sınıfın içindeki temel sınıfta `Getinfo` yöntemi çağırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="618fc-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="618fc-114">Daha fazla örnek için bkz. [New](new-modifier.md), [Virtual](virtual.md)ve [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="618fc-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="618fc-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="618fc-115">Example</span></span>

<span data-ttu-id="618fc-116">Bu örnek, türetilmiş bir sınıfın örneklerini oluştururken çağrılan temel sınıf oluşturucunun nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="618fc-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="618fc-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="618fc-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="618fc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="618fc-118">See also</span></span>

- [<span data-ttu-id="618fc-119">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="618fc-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="618fc-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="618fc-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="618fc-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="618fc-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="618fc-122">this</span><span class="sxs-lookup"><span data-stu-id="618fc-122">this</span></span>](./this.md)
