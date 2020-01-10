---
title: Genel tür parametreleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712188"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="75c70-102">Genel tür parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="75c70-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="75c70-103">Genel tür veya yöntem tanımında bir tür parametresi, bir istemcinin genel türün bir örneğini oluşturduklarında belirttiği belirli bir tür için yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="75c70-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="75c70-104">Genel [türler 'e giriş](./index.md)bölümünde listelenen `GenericList<T>` gibi genel bir sınıf, gerçekten bir tür olmadığından olduğu gibi kullanılamaz; Bu, bir tür için şema gibidir.</span><span class="sxs-lookup"><span data-stu-id="75c70-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="75c70-105">`GenericList<T>`kullanmak için, istemci kodu, açılı ayraç içinde bir tür bağımsız değişkeni belirterek oluşturulmuş bir tür bildirmelidir ve örneklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="75c70-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="75c70-106">Bu belirli sınıfın tür bağımsız değişkeni, derleyici tarafından tanınan herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="75c70-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="75c70-107">Her biri farklı bir tür bağımsız değişkeni kullanılarak oluşturulan herhangi bir sayıda oluşturulmuş tür örneği oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="75c70-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="75c70-108">Bu `GenericList<T>`örneklerinin her birinde, sınıfındaki `T` her bir örneği, tür bağımsız değişkeniyle çalışma zamanında değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="75c70-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="75c70-109">Bu değiştirme yoluyla, tek bir sınıf tanımı kullanarak üç ayrı tür güvenli ve verimli nesne oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="75c70-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="75c70-110">Bu değiştirmenin CLR tarafından nasıl gerçekleştirildiği hakkında daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="75c70-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="75c70-111">Tür parametresi adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="75c70-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="75c70-112">Genel tür parametrelerini açıklayıcı **adlarla adlandırın,** tek bir harf adı tamamen kendi kendine açıklayıcı olamaz ve açıklayıcı bir ad değer eklemez.</span><span class="sxs-lookup"><span data-stu-id="75c70-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="75c70-113">Tek bir harf türü parametresine sahip türler için tür parametre adı olarak T kullanmayı **düşünün** .</span><span class="sxs-lookup"><span data-stu-id="75c70-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="75c70-114">Önek açıklayıcı tür parametre adlarını "T" ile **yapın** .</span><span class="sxs-lookup"><span data-stu-id="75c70-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="75c70-115">Parametre adındaki bir tür parametresine yerleştirilmiş olan kısıtlamaları **belirtmeyi düşünün** .</span><span class="sxs-lookup"><span data-stu-id="75c70-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="75c70-116">Örneğin, `ISession` kısıtlanmış bir parametre `TSession`çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="75c70-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="75c70-117">Kod Analizi kuralı [CA1715](/visualstudio/code-quality/ca1715) , tür parametrelerinin uygun şekilde adlandırılmış olduğundan emin olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75c70-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="75c70-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75c70-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="75c70-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="75c70-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="75c70-120">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="75c70-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="75c70-121">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="75c70-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
