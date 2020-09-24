---
title: Genel yöntemler-C# Programlama Kılavuzu
description: Genel yöntemler olarak bilinen tür parametreleriyle belirtilen yöntemler hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151473"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="9ef98-104">Genel Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9ef98-104">Generic Methods (C# Programming Guide)</span></span>

<span data-ttu-id="9ef98-105">Genel bir yöntem, tür parametreleriyle belirtilen ve aşağıdaki gibi bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="9ef98-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="9ef98-106">Aşağıdaki kod örneği, `int` tür bağımsız değişkeni için kullanarak yöntemini çağırmak için bir yol gösterir:</span><span class="sxs-lookup"><span data-stu-id="9ef98-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="9ef98-107">Ayrıca tür bağımsız değişkenini de atlayabilirsiniz, derleyici onu çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="9ef98-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="9ef98-108">Aşağıdaki çağrısı, `Swap` önceki çağrıya eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="9ef98-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="9ef98-109">Tür çıkarımı için aynı kurallar statik yöntemler ve örnek yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9ef98-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="9ef98-110">Derleyici, tür parametrelerini geçirdiğiniz Yöntem bağımsız değişkenlerine göre çıkarabilir; tür parametreleri yalnızca bir kısıtlamadan veya dönüş değerinden çıkarılamaz.</span><span class="sxs-lookup"><span data-stu-id="9ef98-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="9ef98-111">Bu nedenle tür çıkarımı parametresi olmayan yöntemlerle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="9ef98-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="9ef98-112">Derleyici aşırı yüklenmiş yöntem imzalarını çözmeyi denemeden önce derleme zamanında tür çıkarımı oluşur.</span><span class="sxs-lookup"><span data-stu-id="9ef98-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="9ef98-113">Derleyici, aynı adı paylaşan tüm genel metotlara tür çıkarımı mantığını uygular.</span><span class="sxs-lookup"><span data-stu-id="9ef98-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="9ef98-114">Aşırı yükleme çözümleme adımında, derleyici yalnızca tür çıkarımı başarılı olan genel yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9ef98-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="9ef98-115">Genel bir sınıf içinde genel olmayan yöntemler, sınıf düzeyi tür parametrelerine aşağıdaki gibi erişebilir:</span><span class="sxs-lookup"><span data-stu-id="9ef98-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="9ef98-116">İçerilen sınıfla aynı tür parametrelerini alan genel bir yöntem tanımlarsanız, derleyici yöntem kapsamı içinde uyarı [CS0693](../../misc/cs0693.md) oluşturur, iç için sağlanan bağımsız değişken `T` dıştaki için sağlanan bağımsız değişkeni gizler `T` .</span><span class="sxs-lookup"><span data-stu-id="9ef98-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="9ef98-117">Sınıf örneği oluşturulurken sağlandıklardan farklı tür bağımsız değişkenleriyle bir genel sınıf yöntemi çağırma esnekliğine ihtiyaç duyuyorsanız, aşağıdaki örnekte gösterildiği gibi yönteminin tür parametresi için başka bir tanımlayıcı sağlamayı düşünün `GenericList2<T>` .</span><span class="sxs-lookup"><span data-stu-id="9ef98-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="9ef98-118">Yöntemlerde tür parametrelerinde daha özelleştirilmiş işlemleri sağlamak için kısıtlamaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ef98-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="9ef98-119">`Swap<T>`Artık adlandırılan bu sürümü `SwapIfGreater<T>` Yalnızca uygulayan tür bağımsız değişkenleriyle kullanılabilir <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="9ef98-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="9ef98-120">Genel metotlar çeşitli tür parametrelerinde aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9ef98-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="9ef98-121">Örneğin, aşağıdaki yöntemler aynı sınıfta bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="9ef98-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9ef98-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9ef98-122">C# Language Specification</span></span>  

 <span data-ttu-id="9ef98-123">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="9ef98-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef98-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ef98-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="9ef98-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ef98-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ef98-126">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="9ef98-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="9ef98-127">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9ef98-127">Methods</span></span>](../classes-and-structs/methods.md)
