---
title: Genel tür parametreleri-C# Programlama Kılavuzu
description: C# dilinde genel tür tanımı hakkında bilgi edinin; burada bir tür parametresi, istemcinin genel türün bir örneği için belirttiği bir tür için yer tutucudur.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: dc37029378ac1e9ec194d95b561787761d69a9fd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299259"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="a3d35-103">Genel tür parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a3d35-103">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="a3d35-104">Genel tür veya yöntem tanımında bir tür parametresi, bir istemcinin genel türün bir örneğini oluşturduklarında belirttiği belirli bir tür için yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="a3d35-104">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="a3d35-105">Genel türlere giriş bölümünde listelenen gibi genel bir sınıf, `GenericList<T>` gerçekten bir tür olmadığından olduğu gibi kullanılamaz; bu, bir tür için şema gibi bir değer. [Introduction to Generics](./index.md)</span><span class="sxs-lookup"><span data-stu-id="a3d35-105">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="a3d35-106">Kullanmak için `GenericList<T>` , istemci kodu açılı ayraç içinde bir tür bağımsız değişkeni belirterek oluşturulmuş bir tür bildirmelidir ve örneklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a3d35-106">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="a3d35-107">Bu belirli sınıfın tür bağımsız değişkeni, derleyici tarafından tanınan herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d35-107">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="a3d35-108">Her biri farklı bir tür bağımsız değişkeni kullanılarak oluşturulan herhangi bir sayıda oluşturulmuş tür örneği oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="a3d35-108">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="a3d35-109">Bu örneklerin her birinde `GenericList<T>` , sınıfındaki her oluşum `T` çalışma zamanında tür bağımsız değişkeniyle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a3d35-109">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="a3d35-110">Bu değiştirme yoluyla, tek bir sınıf tanımı kullanarak üç ayrı tür güvenli ve verimli nesne oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="a3d35-110">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="a3d35-111">Bu değiştirmenin CLR tarafından nasıl gerçekleştirildiği hakkında daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="a3d35-111">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="a3d35-112">Tür parametresi adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a3d35-112">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="a3d35-113">Genel tür parametrelerini açıklayıcı **adlarla adlandırın,** tek bir harf adı tamamen kendi kendine açıklayıcı olamaz ve açıklayıcı bir ad değer eklemez.</span><span class="sxs-lookup"><span data-stu-id="a3d35-113">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="a3d35-114">Tek bir harf türü parametresine sahip türler için tür parametre adı olarak T kullanmayı **düşünün** .</span><span class="sxs-lookup"><span data-stu-id="a3d35-114">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="a3d35-115">Önek açıklayıcı tür parametre adlarını "T" ile **yapın** .</span><span class="sxs-lookup"><span data-stu-id="a3d35-115">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="a3d35-116">Parametre adındaki bir tür parametresine yerleştirilmiş olan kısıtlamaları **belirtmeyi düşünün** .</span><span class="sxs-lookup"><span data-stu-id="a3d35-116">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="a3d35-117">Örneğin, ile kısıtlanmış bir parametre `ISession` çağrılabilir `TSession` .</span><span class="sxs-lookup"><span data-stu-id="a3d35-117">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="a3d35-118">Kod Analizi kuralı [CA1715](/visualstudio/code-quality/ca1715) , tür parametrelerinin uygun şekilde adlandırılmış olduğundan emin olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d35-118">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3d35-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3d35-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="a3d35-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a3d35-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a3d35-121">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a3d35-121">Generics</span></span>](./index.md)
- [<span data-ttu-id="a3d35-122">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="a3d35-122">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
