---
title: this (C# Başvurusu)
description: Bu anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 04496079114be45388926993b67e8f1d3f2e9f15
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172041"
---
# <a name="this-c-reference"></a><span data-ttu-id="23501-103">this (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="23501-103">this (C# Reference)</span></span>
<span data-ttu-id="23501-104">`this` Anahtar sözcüğü sınıfının geçerli örneği başvuruyor ve bir ilk parametresi bir genişletme yöntemi değiştirici da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23501-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23501-105">Bu makalede kullanımını ele `this` sınıf örnekleri ile.</span><span class="sxs-lookup"><span data-stu-id="23501-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="23501-106">Kullanımını genişletme yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="23501-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="23501-107">' In yaygın kullanımları şunlardır `this`:</span><span class="sxs-lookup"><span data-stu-id="23501-107">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="23501-108">Benzer adları, örneğin gizli üyeleri nitelemek için:</span><span class="sxs-lookup"><span data-stu-id="23501-108">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="23501-109">Örneğin diğer yöntemleri için bir nesne bir parametre olarak geçirmek için:</span><span class="sxs-lookup"><span data-stu-id="23501-109">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="23501-110">Dizin Oluşturucular, örneğin bildirmek için:</span><span class="sxs-lookup"><span data-stu-id="23501-110">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="23501-111">Statik üye işlevleri, bir nesnenin parçası olarak değil de sınıf düzeyinde olmadıklarından sahip bir `this` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="23501-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="23501-112">Başvurmak için bir hata olduğunu `this` bir statik yöntem.</span><span class="sxs-lookup"><span data-stu-id="23501-112">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23501-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="23501-113">Example</span></span>  
 <span data-ttu-id="23501-114">Bu örnekte, `this` nitelemek için kullanılan `Employee` sınıfı üyelerine, `name` ve `alias`, benzer adlarıyla gizlidir.</span><span class="sxs-lookup"><span data-stu-id="23501-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="23501-115">Bir nesne yönteme de kullanılan `CalcTax`, başka bir sınıfa ait olduğu.</span><span class="sxs-lookup"><span data-stu-id="23501-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="23501-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="23501-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23501-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23501-117">See Also</span></span>  
 [<span data-ttu-id="23501-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="23501-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="23501-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="23501-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="23501-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="23501-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="23501-121">base</span><span class="sxs-lookup"><span data-stu-id="23501-121">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="23501-122">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="23501-122">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
