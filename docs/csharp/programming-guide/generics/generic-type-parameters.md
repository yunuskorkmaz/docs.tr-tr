---
title: Genel tür parametreleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 096fce3affb9461c57ae9c0ffd57367d1b4349df
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423425"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="bc330-102">Genel tür parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bc330-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="bc330-103">Genel tür veya yöntem tanımını bir tür parametresi bir genel türün örneğini oluşturduğunuzda bir istemci belirtir, belirli bir türü için yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="bc330-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="bc330-104">Gibi bir genel sınıf `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/index.md), olarak kullanılamaz-çünkü bu gerçekte bir tür değil; bir tür için bir şema gibi daha fazla.</span><span class="sxs-lookup"><span data-stu-id="bc330-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="bc330-105">Kullanılacak `GenericList<T>`, istemci kodu bildirme ve bir tür bağımsız değişkeni köşeli ayraç içinde belirterek bir oluşturulmuş tür örneği.</span><span class="sxs-lookup"><span data-stu-id="bc330-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="bc330-106">Bu belirli bir sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc330-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="bc330-107">Herhangi bir sayıda oluşturulan tür örnekleri, her biri farklı tür bağımsız değişkeni, kullanarak aşağıdaki gibi oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="bc330-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="bc330-108">Her Bu örneklerin `GenericList<T>`, her geçtiği `T` sınıfı, çalışma zamanında tür bağımsız değişkeni ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc330-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="bc330-109">Bir tek sınıf tanımı kullanarak üç ayrı tür açısından güvenli ve verimli nesneler bu değiştirme yoluyla oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="bc330-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="bc330-110">Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="bc330-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="bc330-111">Tür parametresi adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bc330-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="bc330-112">**Yapmak** tamamen kendi kendine açıklama tek harfli adıdır ve açıklayıcı bir ad, değer ekleme değil sürece genel tür parametreleri Tanımlayıcı adlarla adlandırın.</span><span class="sxs-lookup"><span data-stu-id="bc330-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="bc330-113">**Göz önünde bulundurun** T tek tek harfli türü parametreli türler için tür parametre adı olarak kullanma.</span><span class="sxs-lookup"><span data-stu-id="bc330-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="bc330-114">**Yapmak** açıklayıcı tür parametresi adlarına "T" ile önek.</span><span class="sxs-lookup"><span data-stu-id="bc330-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="bc330-115">**Göz önünde bulundurun** parametre adını bir tür parametresi yerleştirilen kısıtlamaları belirten.</span><span class="sxs-lookup"><span data-stu-id="bc330-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="bc330-116">Örneğin, bir parametre, için kısıtlı `ISession` çağrılabilir `TSession`.</span><span class="sxs-lookup"><span data-stu-id="bc330-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="bc330-117">Kod çözümleme kural [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) tür parametreleri uygun şekilde adlandırıldığından emin olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc330-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc330-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc330-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="bc330-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bc330-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bc330-120">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bc330-120">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="bc330-121">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="bc330-121">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
