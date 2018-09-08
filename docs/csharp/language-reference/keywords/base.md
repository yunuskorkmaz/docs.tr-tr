---
title: Base anahtar sözcüğü (C# Başvurusu)
description: C# türetilmiş bir sınıf içinden temel sınıfın üyelerine erişmek için kullanılan temel anahtar sözcüğü hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 8719ab79273701173530760ad1bec837c4f4302d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180991"
---
# <a name="base-c-reference"></a><span data-ttu-id="b0803-103">base (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0803-103">base (C# Reference)</span></span>

<span data-ttu-id="b0803-104">`base` Anahtar sözcüğü, türetilmiş bir sınıf içinden temel sınıfın üyelerine erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b0803-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="b0803-105">Başka bir yöntem tarafından geçersiz kılınan taban sınıfta bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="b0803-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="b0803-106">Hangi temel sınıf oluşturucusu, türetilmiş sınıf örnekleri oluşturulurken çağrılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="b0803-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="b0803-107">Bir temel sınıf erişim, yalnızca bir oluşturucu, bir örnek yöntemi veya bir örnek özellik erişimcisi izin verilir.</span><span class="sxs-lookup"><span data-stu-id="b0803-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="b0803-108">Kullanılacak bir hata olduğunu `base` anahtar sözcüğü statik bir yöntem içinde.</span><span class="sxs-lookup"><span data-stu-id="b0803-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="b0803-109">Erişilen temel sınıf, sınıf bildiriminde belirtilenden temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b0803-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="b0803-110">Örneğin, belirttiğiniz `class ClassB : ClassA`, Türetilme üyelerinin Türetilme temel sınıfını ne olursa olsun, Sınıfb'den erişilir.</span><span class="sxs-lookup"><span data-stu-id="b0803-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="b0803-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0803-111">Example</span></span>

<span data-ttu-id="b0803-112">Bu örnekte, iki temel sınıfı, `Person`hem de türetilmiş sınıf `Employee`, adında bir yöntemi olan `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="b0803-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="b0803-113">Kullanarak `base` anahtar sözcüğü, mümkündür çağrılacak `Getinfo` içinden temel sınıf yöntemini türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="b0803-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="b0803-114">Diğer örnekler için [yeni](../../../csharp/language-reference/keywords/new.md), [sanal](../../../csharp/language-reference/keywords/virtual.md), ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="b0803-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="b0803-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0803-115">Example</span></span>

<span data-ttu-id="b0803-116">Bu örnek, türetilen bir sınıfın örneklerini oluştururken adlı temel sınıf oluşturucusu belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0803-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="b0803-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b0803-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0803-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0803-118">See also</span></span>

- [<span data-ttu-id="b0803-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b0803-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b0803-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0803-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b0803-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b0803-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="b0803-122">this</span><span class="sxs-lookup"><span data-stu-id="b0803-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)