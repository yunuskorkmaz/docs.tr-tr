---
title: "Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6e60ff600a04dab47e8b0ed52dda00441e17f25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="64aa9-102">Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="64aa9-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="64aa9-103">Dizi Başlatıcı belirtilen öğelerden array örneğine tür çıkarımı yapılan örtük olarak yazılan dizisi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64aa9-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="64aa9-104">Örtük olarak yazılan değişken kuralları örtük olarak yazılan diziler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64aa9-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="64aa9-105">Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="64aa9-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="64aa9-106">Örtük olarak yazılan diziler, genellikle anonim türler ve nesne ve koleksiyon başlatıcıları birlikte sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64aa9-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="64aa9-107">Aşağıdaki örnekler örtük olarak yazılan dizi oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="64aa9-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="64aa9-108">Önceki örnekte, başlatma ifadesinin sol tarafta hiçbir köşeli örtük olarak yazılan diziler ile kullanılan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="64aa9-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="64aa9-109">Basit diziler kullanarak başlatılır ayrıca unutmayın `new []` tek boyutlu diziler'olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="64aa9-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="64aa9-110">Nesne başlatıcıları içindeki örtük olarak yazılan diziler</span><span class="sxs-lookup"><span data-stu-id="64aa9-110">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="64aa9-111">Bir dizi içeren bir anonim türü oluşturduğunuzda, dizi tür nesne Başlatıcı örtülü olarak yazılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="64aa9-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="64aa9-112">Aşağıdaki örnekte, `contacts` her biri içeren adlı bir dizi örtük olarak yazılan anonim türler dizisidir `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="64aa9-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="64aa9-113">Unutmayın `var` anahtar sözcüğü içinde nesne başlatıcıları kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="64aa9-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="64aa9-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64aa9-114">See Also</span></span>  
 [<span data-ttu-id="64aa9-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="64aa9-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="64aa9-116">Örtük olarak yazılan yerel değişkenler</span><span class="sxs-lookup"><span data-stu-id="64aa9-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [<span data-ttu-id="64aa9-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="64aa9-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="64aa9-118">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="64aa9-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="64aa9-119">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="64aa9-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="64aa9-120">var</span><span class="sxs-lookup"><span data-stu-id="64aa9-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="64aa9-121">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="64aa9-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
