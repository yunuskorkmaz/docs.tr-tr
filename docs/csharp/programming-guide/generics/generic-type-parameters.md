---
title: Genel tür parametreleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 48fa90226b7a8a36f5f432921cf5d999e76c6fa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681644"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="f9961-102">Genel Tür Parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f9961-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="f9961-103">Genel tür veya yöntem tanımını bir tür parametreleri olan bir istemci olduğunda bunlar genel türünde bir değişken örneği belirtir, belirli bir tür için bir yer tutucu.</span><span class="sxs-lookup"><span data-stu-id="f9961-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="f9961-104">Gibi bir genel sınıf `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md), olarak kullanılamaz-çünkü bu gerçekte bir tür değil; bir tür için bir şema gibi daha fazla.</span><span class="sxs-lookup"><span data-stu-id="f9961-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="f9961-105">Kullanılacak `GenericList<T>`, istemci kodu bildirme ve bir tür bağımsız değişkeni köşeli ayraç içinde belirterek bir oluşturulmuş tür örneği.</span><span class="sxs-lookup"><span data-stu-id="f9961-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="f9961-106">Bu belirli bir sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9961-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="f9961-107">Herhangi bir sayıda oluşturulan tür örnekleri, her biri farklı tür bağımsız değişkeni, kullanarak aşağıdaki gibi oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="f9961-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 <span data-ttu-id="f9961-108">Her Bu örneklerin `GenericList<T>`, her geçtiği `T` sınıfı, çalışma zamanında tür bağımsız değişkeni ile değiştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="f9961-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="f9961-109">Bir tek sınıf tanımı kullanarak üç ayrı tür açısından güvenli ve verimli nesneler bu değiştirme yoluyla oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="f9961-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="f9961-110">Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="f9961-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="f9961-111">Tür parametresi adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="f9961-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="f9961-112">**Yapmak** tamamen kendi kendine açıklama tek harfli adıdır ve açıklayıcı bir ad, değer ekleme değil sürece genel tür parametreleri Tanımlayıcı adlarla adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f9961-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   <span data-ttu-id="f9961-113">**Göz önünde bulundurun** T tek tek harfli türü parametreli türler için tür parametre adı olarak kullanma.</span><span class="sxs-lookup"><span data-stu-id="f9961-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   <span data-ttu-id="f9961-114">**Yapmak** açıklayıcı tür parametresi adlarına "T" ile önek.</span><span class="sxs-lookup"><span data-stu-id="f9961-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   <span data-ttu-id="f9961-115">**Göz önünde bulundurun** parametre adını bir tür parametresi yerleştirilen kısıtlamaları belirten.</span><span class="sxs-lookup"><span data-stu-id="f9961-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="f9961-116">Örneğin, bir parametre, için kısıtlı `ISession` çağrılabilir `TSession`.</span><span class="sxs-lookup"><span data-stu-id="f9961-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9961-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9961-117">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="f9961-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9961-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f9961-119">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f9961-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="f9961-120">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="f9961-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
