---
title: "Genel Yöntemler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63252dbe4307889f57d35e23eb0575f84358d737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="76e88-102">Genel Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="76e88-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="76e88-103">Genel yöntem tür parametreleri ile aşağıdaki gibi bildirilmiş bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="76e88-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="76e88-104">Aşağıdaki kod örneği kullanarak yöntemini çağırmak için bir yolunu gösterir `int` tür bağımsız değişkeni için:</span><span class="sxs-lookup"><span data-stu-id="76e88-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="76e88-105">Tür bağımsız değişkeni de atlayabilirsiniz ve derleyici Infer.</span><span class="sxs-lookup"><span data-stu-id="76e88-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="76e88-106">Aşağıdaki çağrı `Swap` önceki çağrısına eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="76e88-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="76e88-107">Tür çıkarımı için aynı kuralları statik yöntemler ve örnek yöntemleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="76e88-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="76e88-108">Derleyici, geçirdiğiniz yöntem bağımsız değişkenleri temel tür parametreleri çıkarımını; Tür parametreleri yalnızca bir kısıtlama gelen Infer veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="76e88-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="76e88-109">Bu nedenle tür çıkarımı parametresi olmayan yöntemleriyle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="76e88-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="76e88-110">Tür çıkarımı derleyici aşırı yüklenmiş yöntemin imzaları çözümlemeye önce derleme zamanında oluşur.</span><span class="sxs-lookup"><span data-stu-id="76e88-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="76e88-111">Derleyici aynı adı paylaşan tüm genel yöntemler tür çıkarımı mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="76e88-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="76e88-112">Aşırı yükleme çözümü adımda Derleyici yalnızca üzerinde tür çıkarımı başarılı genel yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="76e88-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="76e88-113">Genel bir sınıf içinde genel olmayan yöntemleri sınıf düzeyi tür parametreleri aşağıdaki gibi erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76e88-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="76e88-114">Aynı tür parametreleri içeren sınıf gereken genel bir yöntem tanımlarsanız yöntemi kapsamında bağımsız değişkeni için iç sağladığından derleyici uyarı CS0693 oluşturur `T` dış içinsağlananbağımsızdeğişkengizler`T`.</span><span class="sxs-lookup"><span data-stu-id="76e88-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="76e88-115">Tür bağımsız değişkenleri sınıfı örneğinin başlatılmasından çalıştırılırken sağlanan dışındaki genel sınıfı yöntemiyle çağırma esnekliğini gerektiriyorsa, başka bir tanımlayıcı yöntemi tür parametresi için sağlamayı gösterildiği gibi düşünün `GenericList2<T>` aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="76e88-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="76e88-116">Tür parametrelerindeki yöntemler daha özelleştirilmiş işlemlerini etkinleştirmek için kısıtlamaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="76e88-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="76e88-117">Bu sürümü `Swap<T>`, şimdi adlandırılmış `SwapIfGreater<T>`, yalnızca uygulama tür bağımsız değişkenleri ile kullanılabilir <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="76e88-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="76e88-118">Genel yöntemler birkaç türü parametrelerine aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="76e88-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="76e88-119">Örneğin, aşağıdaki yöntemlerden tümü aynı sınıfta bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="76e88-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="76e88-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="76e88-120">C# Language Specification</span></span>  
 <span data-ttu-id="76e88-121">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="76e88-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e88-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76e88-122">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="76e88-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="76e88-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="76e88-124">Genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="76e88-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="76e88-125">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="76e88-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
