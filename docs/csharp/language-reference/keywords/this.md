---
title: this (C# Başvurusu)
description: Bu anahtar sözcüğü (C# Başvurusu)
keywords: Bu (C#), bu anahtar sözcüğü (C#), bu anahtar sözcüğü (C# Başvurusu), bu anahtar sözcüğü (C# dili Başvurusu)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="5499e-104">this (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5499e-104">this (C# Reference)</span></span>
<span data-ttu-id="5499e-105">`this` Anahtar sözcüğü sınıfının geçerli örneği başvuruyor ve bir ilk parametresi bir genişletme yöntemi değiştirici da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5499e-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5499e-106">Bu makalede kullanımını ele `this` sınıf örnekleri ile.</span><span class="sxs-lookup"><span data-stu-id="5499e-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="5499e-107">Kullanımını genişletme yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5499e-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="5499e-108">' In yaygın kullanımları şunlardır `this`:</span><span class="sxs-lookup"><span data-stu-id="5499e-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="5499e-109">Benzer adları, örneğin gizli üyeleri nitelemek için:</span><span class="sxs-lookup"><span data-stu-id="5499e-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="5499e-110">Örneğin diğer yöntemleri için bir nesne bir parametre olarak geçirmek için:</span><span class="sxs-lookup"><span data-stu-id="5499e-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="5499e-111">Dizin Oluşturucular, örneğin bildirmek için:</span><span class="sxs-lookup"><span data-stu-id="5499e-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="5499e-112">Statik üye işlevleri, bir nesnenin parçası olarak değil de sınıf düzeyinde olmadıklarından sahip bir `this` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5499e-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="5499e-113">Başvurmak için bir hata olduğunu `this` bir statik yöntem.</span><span class="sxs-lookup"><span data-stu-id="5499e-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5499e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5499e-114">Example</span></span>  
 <span data-ttu-id="5499e-115">Bu örnekte, `this` nitelemek için kullanılan `Employee` sınıfı üyelerine, `name` ve `alias`, benzer adlarıyla gizlidir.</span><span class="sxs-lookup"><span data-stu-id="5499e-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="5499e-116">Bir nesne yönteme de kullanılan `CalcTax`, başka bir sınıfa ait olduğu.</span><span class="sxs-lookup"><span data-stu-id="5499e-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5499e-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5499e-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5499e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5499e-118">See Also</span></span>  
 [<span data-ttu-id="5499e-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5499e-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5499e-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5499e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5499e-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5499e-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5499e-122">temel</span><span class="sxs-lookup"><span data-stu-id="5499e-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="5499e-123">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="5499e-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
