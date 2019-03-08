---
title: Genel tür parametreleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 10feb47ce3dfe9e356da381e0d62e6d220c9452a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677428"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="5e084-102">Genel tür parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5e084-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="5e084-103">Genel tür veya yöntem tanımını bir tür parametresi bir genel türün örneğini oluşturduğunuzda bir istemci belirtir, belirli bir türü için yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="5e084-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="5e084-104">Gibi bir genel sınıf `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md), olarak kullanılamaz-çünkü bu gerçekte bir tür değil; bir tür için bir şema gibi daha fazla.</span><span class="sxs-lookup"><span data-stu-id="5e084-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="5e084-105">Kullanılacak `GenericList<T>`, istemci kodu bildirme ve bir tür bağımsız değişkeni köşeli ayraç içinde belirterek bir oluşturulmuş tür örneği.</span><span class="sxs-lookup"><span data-stu-id="5e084-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="5e084-106">Bu belirli bir sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e084-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="5e084-107">Herhangi bir sayıda oluşturulan tür örnekleri, her biri farklı tür bağımsız değişkeni, kullanarak aşağıdaki gibi oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="5e084-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="5e084-108">Her Bu örneklerin `GenericList<T>`, her geçtiği `T` sınıfı, çalışma zamanında tür bağımsız değişkeni ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="5e084-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="5e084-109">Bir tek sınıf tanımı kullanarak üç ayrı tür açısından güvenli ve verimli nesneler bu değiştirme yoluyla oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="5e084-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="5e084-110">Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="5e084-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="5e084-111">Tür parametresi adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="5e084-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="5e084-112">**Yapmak** tamamen kendi kendine açıklama tek harfli adıdır ve açıklayıcı bir ad, değer ekleme değil sürece genel tür parametreleri Tanımlayıcı adlarla adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5e084-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="5e084-113">**Göz önünde bulundurun** T tek tek harfli türü parametreli türler için tür parametre adı olarak kullanma.</span><span class="sxs-lookup"><span data-stu-id="5e084-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="5e084-114">**Yapmak** açıklayıcı tür parametresi adlarına "T" ile önek.</span><span class="sxs-lookup"><span data-stu-id="5e084-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="5e084-115">**Göz önünde bulundurun** parametre adını bir tür parametresi yerleştirilen kısıtlamaları belirten.</span><span class="sxs-lookup"><span data-stu-id="5e084-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="5e084-116">Örneğin, bir parametre, için kısıtlı `ISession` çağrılabilir `TSession`.</span><span class="sxs-lookup"><span data-stu-id="5e084-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="5e084-117">Kod çözümleme kural [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) tür parametreleri uygun şekilde adlandırıldığından emin olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e084-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5e084-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e084-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="5e084-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e084-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5e084-120">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5e084-120">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="5e084-121">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="5e084-121">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
