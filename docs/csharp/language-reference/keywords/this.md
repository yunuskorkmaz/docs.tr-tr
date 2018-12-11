---
title: Bu anahtar sözcüğü (C# Başvurusu)
description: Bu anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 52e7fce0ebeeccfbf5f56dbbcade9fae2890dfe1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130826"
---
# <a name="this-c-reference"></a><span data-ttu-id="b34a5-103">this (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b34a5-103">this (C# Reference)</span></span>

<span data-ttu-id="b34a5-104">`this` Anahtar sözcüğü sınıfın geçerli örneğine başvurur ve genişletme yönteminin ilk parametresinin bir değiştirici da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b34a5-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="b34a5-105">Bu makalede kullanımı ele alınmaktadır `this` sınıf örneğine sahip.</span><span class="sxs-lookup"><span data-stu-id="b34a5-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="b34a5-106">Kullanımını genişletme yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b34a5-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="b34a5-107">' In yaygın kullanımları şunlardır `this`:</span><span class="sxs-lookup"><span data-stu-id="b34a5-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="b34a5-108">Örneğin benzer adlarla gizli üyeleri nitelemek için:</span><span class="sxs-lookup"><span data-stu-id="b34a5-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="b34a5-109">Diğer yöntemleri için parametre olarak nesne örneğin iletmek için:</span><span class="sxs-lookup"><span data-stu-id="b34a5-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="b34a5-110">Dizin Oluşturucular, örneğin bildirmek için:</span><span class="sxs-lookup"><span data-stu-id="b34a5-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="b34a5-111">Bir nesnenin parçası olarak değil de sınıf düzeyinde olduğundan statik üye işlevleri yoktur bir `this` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b34a5-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="b34a5-112">Başvurmak için bir hata olduğunu `this` statik yöntemde.</span><span class="sxs-lookup"><span data-stu-id="b34a5-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="b34a5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b34a5-113">Example</span></span>

<span data-ttu-id="b34a5-114">Bu örnekte, `this` nitelemek için kullanılan `Employee` sınıf üyeleri, `name` ve `alias`, benzer adlarla gizlidir.</span><span class="sxs-lookup"><span data-stu-id="b34a5-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="b34a5-115">Bir nesne yönteme geçirmek için de kullanılır `CalcTax`, başka bir sınıfa aittir.</span><span class="sxs-lookup"><span data-stu-id="b34a5-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="b34a5-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b34a5-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b34a5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b34a5-117">See also</span></span>

- [<span data-ttu-id="b34a5-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b34a5-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b34a5-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b34a5-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b34a5-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b34a5-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b34a5-121">base</span><span class="sxs-lookup"><span data-stu-id="b34a5-121">base</span></span>](base.md)
- [<span data-ttu-id="b34a5-122">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b34a5-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
