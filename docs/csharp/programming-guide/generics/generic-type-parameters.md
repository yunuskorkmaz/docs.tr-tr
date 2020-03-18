---
title: Genel Tip Parametreler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712188"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="ced64-102">Genel tür parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ced64-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="ced64-103">Genel bir tür veya yöntem tanımında, tür parametresi, istemcinin genel türün bir örneğini oluştururken belirttiği belirli bir tür için bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="ced64-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="ced64-104">Genel Lere `GenericList<T>` [Giriş'te](./index.md)listelenen genel bir sınıf, gerçekten bir tür olmadığı için olduğu gibi kullanılamaz; daha çok bir tür için bir plan gibidir.</span><span class="sxs-lookup"><span data-stu-id="ced64-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="ced64-105">Kullanmak `GenericList<T>`için, istemci kodu açı parantez içinde bir tür bağımsız değişkeni belirterek oluşturulmuş bir türü bildirmek ve anlık olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ced64-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="ced64-106">Bu sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="ced64-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="ced64-107">Oluşturulan tür örnekleri, her biri farklı bir tür bağımsız değişkeni kullanarak, aşağıdaki gibi oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="ced64-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="ced64-108">Bu örneklerin her `GenericList<T>`birinde, sınıftaki `T` her oluşum çalışma zamanında tür bağımsız değişkeni ile ikame edilir.</span><span class="sxs-lookup"><span data-stu-id="ced64-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="ced64-109">Bu ikame sayesinde, tek bir sınıf tanımı kullanarak üç ayrı tür güvenli ve verimli nesneler oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="ced64-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="ced64-110">Bu ikame clr tarafından nasıl gerçekleştirildiği hakkında daha fazla bilgi [için, Run Time'daki Genel Bilgiler'e](./generics-in-the-run-time.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ced64-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="ced64-111">Parametre adlandırma yönergeleri yazın</span><span class="sxs-lookup"><span data-stu-id="ced64-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="ced64-112">**Do** Tek bir harf adı tamamen açıklayıcı ve açıklayıcı bir ad değer eklemez sürece, açıklayıcı adlarla genel tür parametreleri adlandırın.</span><span class="sxs-lookup"><span data-stu-id="ced64-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="ced64-113">Tek harf türü parametresi olan türler için tür parametresi adı olarak T'yi kullanmayı **düşünün.**</span><span class="sxs-lookup"><span data-stu-id="ced64-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="ced64-114">"T" ile açıklayıcı tür parametre adları önek **yapın.**</span><span class="sxs-lookup"><span data-stu-id="ced64-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="ced64-115">Parametre adına bir tür parametresine yerleştirilen kısıtlamaları belirtmeyi **düşünün.**</span><span class="sxs-lookup"><span data-stu-id="ced64-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="ced64-116">Örneğin, sınırlandırılmış `ISession` bir parametre . `TSession`</span><span class="sxs-lookup"><span data-stu-id="ced64-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="ced64-117">Kod çözümleme kuralı [CA1715,](/visualstudio/code-quality/ca1715) tür parametrelerinin uygun şekilde adlandırılmasını sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ced64-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ced64-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ced64-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="ced64-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ced64-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ced64-120">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ced64-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="ced64-121">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="ced64-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
