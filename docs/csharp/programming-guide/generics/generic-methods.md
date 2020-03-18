---
title: Genel Yöntemler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712201"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="c07fd-102">Genel Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c07fd-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="c07fd-103">Genel bir yöntem, tür parametreleri ile bildirilen bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="c07fd-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="c07fd-104">Aşağıdaki kod örneği, tür bağımsız değişkeni `int` için kullanarak yöntemi çağırmanın bir yolunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="c07fd-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="c07fd-105">Ayrıca tür bağımsız değişkenini atlayabilirsiniz ve derleyici bunu çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="c07fd-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="c07fd-106">Aşağıdaki arama `Swap` önceki çağrıya eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="c07fd-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="c07fd-107">Tür çıkarım için aynı kurallar statik yöntemler ve örnek yöntemleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c07fd-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="c07fd-108">Derleyici, geçiş yaptığınız yöntem bağımsız değişkenlerine göre tür parametrelerini çıkartabilir; tür parametrelerini yalnızca bir kısıtlama veya geri dönüş değerinden çıkaramaz.</span><span class="sxs-lookup"><span data-stu-id="c07fd-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="c07fd-109">Bu nedenle tür çıkarım hiçbir parametre si olmayan yöntemlerle çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="c07fd-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="c07fd-110">Tür çıkarımı, derleyici aşırı yüklenen yöntem imzalarını çözmeye çalışmadan önce derleme zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c07fd-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="c07fd-111">Derleyici, aynı adı paylaşan tüm genel yöntemlere tür çıkarım mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="c07fd-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="c07fd-112">Aşırı yük çözümlemesi adımında derleyici yalnızca tür çıkarımlarında başarılı olan genel yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c07fd-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="c07fd-113">Genel bir sınıf içinde, genel olmayan yöntemler sınıf düzeyi türü parametrelerine aşağıdaki gibi erişebilir:</span><span class="sxs-lookup"><span data-stu-id="c07fd-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="c07fd-114">İçerdiği sınıfla aynı tür parametrelerini alan genel bir yöntem tanımlarsanız, derleyici [cs0693](../../misc/cs0693.md) uyarısı üretir, `T` çünkü yöntem kapsamı içinde, `T`iç için sağlanan bağımsız değişken dış için sağlanan bağımsız değişkeni gizler.</span><span class="sxs-lookup"><span data-stu-id="c07fd-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="c07fd-115">Sınıf anında yapıldığında sağlananlar dışındaki tür bağımsız değişkenleri ile genel bir sınıf yöntemini çağırma esnekliğine ihtiyaç duyuyorsanız, aşağıdaki örnekte `GenericList2<T>` gösterildiği gibi yöntemin tür parametresi için başka bir tanımlayıcı sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c07fd-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="c07fd-116">Yöntemlerdeki tür parametreleri üzerinde daha özel işlemler etkinleştirmek için kısıtlamaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="c07fd-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="c07fd-117">Şimdi adlandırılmış `Swap<T>` `SwapIfGreater<T>`olan bu sürüm yalnızca uygulayan <xref:System.IComparable%601>tür bağımsız değişkenleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c07fd-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="c07fd-118">Genel yöntemler çeşitli tür parametreleri üzerinde aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c07fd-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="c07fd-119">Örneğin, aşağıdaki yöntemlerin tümü aynı sınıfta bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="c07fd-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c07fd-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c07fd-120">C# Language Specification</span></span>  
 <span data-ttu-id="c07fd-121">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="c07fd-121">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07fd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c07fd-122">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="c07fd-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c07fd-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c07fd-124">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="c07fd-124">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="c07fd-125">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c07fd-125">Methods</span></span>](../classes-and-structs/methods.md)
