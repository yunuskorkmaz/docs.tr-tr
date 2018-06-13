---
title: Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 60d320b233986154c3c51c409bade24d0862dedd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315210"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="e3fed-102">Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e3fed-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="e3fed-103">Dizi Başlatıcı belirtilen öğelerden array örneğine tür çıkarımı yapılan örtük olarak yazılan dizisi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3fed-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="e3fed-104">Örtük olarak yazılan değişken kuralları örtük olarak yazılan diziler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e3fed-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="e3fed-105">Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="e3fed-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="e3fed-106">Örtük olarak yazılan diziler, genellikle anonim türler ve nesne ve koleksiyon başlatıcıları birlikte sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3fed-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="e3fed-107">Aşağıdaki örnekler örtük olarak yazılan dizi oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e3fed-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="e3fed-108">Önceki örnekte, başlatma ifadesinin sol tarafta hiçbir köşeli örtük olarak yazılan diziler ile kullanılan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e3fed-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="e3fed-109">Basit diziler kullanarak başlatılır ayrıca unutmayın `new []` tek boyutlu diziler'olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="e3fed-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="e3fed-110">Nesne başlatıcıları içindeki örtük olarak yazılan diziler</span><span class="sxs-lookup"><span data-stu-id="e3fed-110">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="e3fed-111">Bir dizi içeren bir anonim türü oluşturduğunuzda, dizi tür nesne Başlatıcı örtülü olarak yazılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3fed-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="e3fed-112">Aşağıdaki örnekte, `contacts` her biri içeren adlı bir dizi örtük olarak yazılan anonim türler dizisidir `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="e3fed-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="e3fed-113">Unutmayın `var` anahtar sözcüğü içinde nesne başlatıcıları kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e3fed-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e3fed-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3fed-114">See Also</span></span>  
 [<span data-ttu-id="e3fed-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e3fed-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3fed-116">Örtülü Olarak Yazılan Yerel Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e3fed-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [<span data-ttu-id="e3fed-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="e3fed-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="e3fed-118">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="e3fed-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="e3fed-119">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e3fed-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="e3fed-120">var</span><span class="sxs-lookup"><span data-stu-id="e3fed-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="e3fed-121">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e3fed-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
