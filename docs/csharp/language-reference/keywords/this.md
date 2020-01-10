---
title: this anahtar sözcüğü C# başvurusu
description: this anahtar sözcüğüC# (başvuru)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715104"
---
# <a name="this-c-reference"></a><span data-ttu-id="a0250-103">this (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a0250-103">this (C# Reference)</span></span>

<span data-ttu-id="a0250-104">`this` anahtar sözcüğü, sınıfın geçerli örneğine başvurur ve bir genişletme yönteminin ilk parametresi için bir değiştirici olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0250-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="a0250-105">Bu makalede, sınıf örnekleriyle `this` kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0250-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="a0250-106">Uzantı yöntemlerinde kullanımı hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a0250-106">For more information about its use in extension methods, see [Extension Methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="a0250-107">Aşağıda `this`yaygın kullanımları verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a0250-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="a0250-108">Benzer adlarla gizlenen üyeleri nitelemek için, örneğin:</span><span class="sxs-lookup"><span data-stu-id="a0250-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="a0250-109">Bir nesneyi diğer yöntemlere parametre olarak geçirmek için, örneğin:</span><span class="sxs-lookup"><span data-stu-id="a0250-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="a0250-110">Dizin oluşturucular bildirmek için örneğin:</span><span class="sxs-lookup"><span data-stu-id="a0250-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="a0250-111">Statik üye işlevleri, sınıf düzeyinde olduklarından ve bir nesnenin parçası olarak olmadığından, `this` işaretçisine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a0250-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="a0250-112">Statik bir yöntemde `this` başvurmak hatadır.</span><span class="sxs-lookup"><span data-stu-id="a0250-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="a0250-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0250-113">Example</span></span>

<span data-ttu-id="a0250-114">Bu örnekte `this`, benzer adlarla gizlenen `name` ve `alias``Employee` sınıf üyelerini nitelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0250-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="a0250-115">Ayrıca, bir nesneyi başka bir sınıfa ait `CalcTax`yönteme geçirmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0250-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="a0250-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a0250-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a0250-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0250-117">See also</span></span>

- [<span data-ttu-id="a0250-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="a0250-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a0250-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a0250-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a0250-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a0250-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a0250-121">base</span><span class="sxs-lookup"><span data-stu-id="a0250-121">base</span></span>](base.md)
- [<span data-ttu-id="a0250-122">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a0250-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
