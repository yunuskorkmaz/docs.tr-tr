---
title: Genel yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 443d4367cc64eb7f9054b2cd52bef59e589f55b3
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170253"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="5bd1d-102">Genel Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5bd1d-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="5bd1d-103">Genel bir yöntem tür parametreleri ile aşağıdaki gibi belirtilen bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="5bd1d-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="5bd1d-104">Aşağıdaki kod örneği kullanarak yöntemini çağırma yollarından biri gösterilmektedir `int` tür bağımsız değişkeni için:</span><span class="sxs-lookup"><span data-stu-id="5bd1d-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="5bd1d-105">Tür bağımsız değişkeni de atlayabilirsiniz ve derleyici bunu çıkarımlar.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="5bd1d-106">Aşağıdaki çağrı `Swap` önceki çağrısına eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="5bd1d-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="5bd1d-107">Tür çıkarımı için aynı kurallara statik ve örnek yöntemleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="5bd1d-108">Derleyici, geçirdiğiniz yöntem bağımsız değişkenleri temel tür parametreleri çıkarımını; Kısıtlama türü Parametreler yalnızca tanım Çıkarsama veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="5bd1d-109">Bu nedenle tür çıkarımı, parametresi olmayan yöntemleri ile çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="5bd1d-110">Tür çıkarımı, derleyici aşırı yüklenmiş yöntem imzaları çözmeye çalışmadan önce derleme zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="5bd1d-111">Derleyicinin tür çıkarımı mantıksal aynı adı paylaşan tüm genel yöntemleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="5bd1d-112">Aşırı yükleme çözünürlüğü adımda yalnızca üzerinde tür çıkarımı başarılı genel yöntemler derleyicisini içerir.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="5bd1d-113">Genel bir sınıf içinde genel olmayan yöntemler sınıf düzeyinde tür parametreleri gibi erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5bd1d-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="5bd1d-114">Kapsayan sınıfı aynı tür parametreleri alan genel yöntem tanımlama, derleyicinin uyarı oluşturur. [CS0693](../../misc/cs0693.md) yöntemi kapsamında, bağımsız değişken için iç sağladığından `T` bağımsız değişkenini gizler Dış için sağlanan `T`.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="5bd1d-115">Tür bağımsız değişkenleri sınıfı oluşturulduğunda sağlanan olanlar dışındaki bir genel sınıfı yöntemini çağırma esneklik gerekiyorsa, başka bir tanımlayıcı yöntem türü parametresi sağlamayı gösterildiği gibi düşünün `GenericList2<T>` aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="5bd1d-116">Kısıtlama yöntemlerini tür parametrelerindeki daha özel işlemlerini etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="5bd1d-117">Bu sürümü `Swap<T>`, artık adlandırılmış `SwapIfGreater<T>`, uygulama tür bağımsız değişkenleri ile yalnızca kullanılabilir <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="5bd1d-118">Birden çok tür parametrelerinde genel yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="5bd1d-119">Örneğin, aşağıdaki yöntemlerden tümü aynı sınıf içinde yer alabilir:</span><span class="sxs-lookup"><span data-stu-id="5bd1d-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5bd1d-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5bd1d-120">C# Language Specification</span></span>  
 <span data-ttu-id="5bd1d-121">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="5bd1d-121">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd1d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bd1d-122">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="5bd1d-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5bd1d-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5bd1d-124">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="5bd1d-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="5bd1d-125">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5bd1d-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
