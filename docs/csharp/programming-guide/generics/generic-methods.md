---
title: Genel yöntemler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712201"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="bb9cc-102">Genel Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb9cc-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="bb9cc-103">Genel bir yöntem, tür parametreleriyle belirtilen ve aşağıdaki gibi bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="bb9cc-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="bb9cc-104">Aşağıdaki kod örneği, tür bağımsız değişkeni için `int` kullanarak yöntemi çağırmak için bir yol gösterir:</span><span class="sxs-lookup"><span data-stu-id="bb9cc-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="bb9cc-105">Ayrıca tür bağımsız değişkenini de atlayabilirsiniz, derleyici onu çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="bb9cc-106">Aşağıdaki `Swap` çağrısı, önceki çağrıya eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="bb9cc-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="bb9cc-107">Tür çıkarımı için aynı kurallar statik yöntemler ve örnek yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="bb9cc-108">Derleyici, tür parametrelerini geçirdiğiniz Yöntem bağımsız değişkenlerine göre çıkarabilir; tür parametreleri yalnızca bir kısıtlamadan veya dönüş değerinden çıkarılamaz.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="bb9cc-109">Bu nedenle tür çıkarımı parametresi olmayan yöntemlerle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="bb9cc-110">Derleyici aşırı yüklenmiş yöntem imzalarını çözmeyi denemeden önce derleme zamanında tür çıkarımı oluşur.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="bb9cc-111">Derleyici, aynı adı paylaşan tüm genel metotlara tür çıkarımı mantığını uygular.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="bb9cc-112">Aşırı yükleme çözümleme adımında, derleyici yalnızca tür çıkarımı başarılı olan genel yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="bb9cc-113">Genel bir sınıf içinde genel olmayan yöntemler, sınıf düzeyi tür parametrelerine aşağıdaki gibi erişebilir:</span><span class="sxs-lookup"><span data-stu-id="bb9cc-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="bb9cc-114">İçerilen sınıfla aynı tür parametrelerini alan genel bir yöntem tanımlarsanız, derleyici [CS0693](../../misc/cs0693.md) uyarı oluşturur, çünkü Yöntem kapsamı içinde, iç `T` sağlanan bağımsız değişken dış `T`için sağlanan bağımsız değişkeni gizler.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="bb9cc-115">Sınıf örneği oluşturulurken sağlananlara farklı tür bağımsız değişkenleriyle bir genel sınıf yöntemi çağırma esnekliğine ihtiyaç duyuyorsanız, aşağıdaki örnekte `GenericList2<T>` gösterildiği gibi yönteminin tür parametresi için başka bir tanımlayıcı sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="bb9cc-116">Yöntemlerde tür parametrelerinde daha özelleştirilmiş işlemleri sağlamak için kısıtlamaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="bb9cc-117">Artık `SwapIfGreater<T>`olarak adlandırılan bu `Swap<T>`sürümü yalnızca <xref:System.IComparable%601>uygulayan tür bağımsız değişkenleriyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="bb9cc-118">Genel metotlar çeşitli tür parametrelerinde aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="bb9cc-119">Örneğin, aşağıdaki yöntemler aynı sınıfta bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="bb9cc-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb9cc-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="bb9cc-120">C# Language Specification</span></span>  
 <span data-ttu-id="bb9cc-121">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="bb9cc-121">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9cc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb9cc-122">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="bb9cc-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb9cc-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bb9cc-124">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="bb9cc-124">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="bb9cc-125">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bb9cc-125">Methods</span></span>](../classes-and-structs/methods.md)
