---
title: bu anahtar kelime - C# Reference
description: bu anahtar kelime (C# Reference)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715104"
---
# <a name="this-c-reference"></a><span data-ttu-id="5915c-103">this (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5915c-103">this (C# Reference)</span></span>

<span data-ttu-id="5915c-104">`this` Anahtar kelime sınıfın geçerli örneğine başvurur ve bir uzantı yönteminin ilk parametresini değiştirici olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5915c-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="5915c-105">Bu makalede sınıf örnekleri `this` ile kullanımı anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5915c-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="5915c-106">Uzantı yöntemlerinin kullanımı hakkında daha fazla bilgi için [Uzantı Yöntemleri'ne](../../programming-guide/classes-and-structs/extension-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5915c-106">For more information about its use in extension methods, see [Extension Methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="5915c-107">Aşağıdaki ortak kullanımları `this`şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5915c-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="5915c-108">Benzer adlarla gizlenen üyeleri nitelemek için:</span><span class="sxs-lookup"><span data-stu-id="5915c-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="5915c-109">Bir nesneyi parametre olarak diğer yöntemlere aktarmak için, örneğin:</span><span class="sxs-lookup"><span data-stu-id="5915c-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="5915c-110">Dizinleyicileri bildirmek için, örneğin:</span><span class="sxs-lookup"><span data-stu-id="5915c-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="5915c-111">Statik üye işlevler, bir nesnenin parçası olarak değil, sınıf düzeyinde `this` var olduğundan, bir işaretçi yok.</span><span class="sxs-lookup"><span data-stu-id="5915c-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="5915c-112">Statik bir `this` yöntemde başvurmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="5915c-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="5915c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="5915c-113">Example</span></span>

<span data-ttu-id="5915c-114">`this` Bu örnekte, `Employee` sınıf üyelerini nitelemek `name` `alias`için kullanılır ve benzer adlarla gizlenir.</span><span class="sxs-lookup"><span data-stu-id="5915c-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="5915c-115">Ayrıca, başka bir sınıfa ait yönteme `CalcTax`bir nesne geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5915c-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="5915c-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5915c-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5915c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5915c-117">See also</span></span>

- [<span data-ttu-id="5915c-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="5915c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5915c-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5915c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5915c-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="5915c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5915c-121">base</span><span class="sxs-lookup"><span data-stu-id="5915c-121">base</span></span>](base.md)
- [<span data-ttu-id="5915c-122">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5915c-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
