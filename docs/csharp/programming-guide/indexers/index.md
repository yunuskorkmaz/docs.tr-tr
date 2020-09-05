---
title: Dizin oluşturucular-C# Programlama Kılavuzu
description: C# içindeki dizin oluşturucular, sınıf veya yapı örneklerinin diziler gibi dizine eklenmesine Izin verir. Dizinli değeri bir tür veya örnek üyesi belirtmeden ayarlayabilir veya alabilirsiniz.
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: ea95eef7bb9ba232e4d59e3f833b82e98398fc33
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495310"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="ef7d9-104">Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ef7d9-104">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="ef7d9-105">Dizin oluşturucular, bir sınıf veya yapının örneklerinin, tıpkı diziler gibi dizine eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-105">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="ef7d9-106">Dizinli değer, açıkça bir tür veya örnek üyesi belirtilmeden ayarlanabilir veya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-106">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="ef7d9-107">Dizin oluşturucular, erişimcilerinin parametre kazanması dışında [özelliklere](../classes-and-structs/properties.md) benzer.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-107">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="ef7d9-108">Aşağıdaki örnek, değer atamak ve almak için basit [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcisi yöntemleriyle genel bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-108">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="ef7d9-109">`Program`Sınıfı dizeleri depolamak için bu sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-109">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="ef7d9-110">Daha fazla örnek için bkz. [Ilgili bölümler](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="ef7d9-110">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="ef7d9-111">İfade gövdesi tanımları</span><span class="sxs-lookup"><span data-stu-id="ef7d9-111">Expression Body Definitions</span></span>  

<span data-ttu-id="ef7d9-112">Bir dizin oluşturucunun Get veya set erişimcisinin bir değer döndüren ya da ayarlayan tek bir deyimden oluşması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-112">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="ef7d9-113">İfade-Bodied Üyeler, bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-113">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="ef7d9-114">C# 6 ' dan itibaren, aşağıdaki örnekte gösterildiği gibi, bir salt okuma Dizin Oluşturucu ifade olarak uygulanabilir üye olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-114">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="ef7d9-115">`=>`İfade gövdesini tanıtır ve `get` anahtar sözcüğünün kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="ef7d9-116">C# 7,0 ' den itibaren hem Get hem de set erişimcisi, ifade Bodied Üyeler olarak uygulanan bir uygulanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-116">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="ef7d9-117">Bu durumda, hem hem `get` de `set` anahtar sözcüklerin kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="ef7d9-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef7d9-118">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="ef7d9-119">Dizin Oluşturuculara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ef7d9-119">Indexers Overview</span></span>  
  
- <span data-ttu-id="ef7d9-120">Dizin oluşturucular, nesnelerin dizilere benzer bir şekilde dizine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-120">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="ef7d9-121">`get`Erişimci bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-121">A `get` accessor returns a value.</span></span> <span data-ttu-id="ef7d9-122">`set`Erişimci bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-122">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="ef7d9-123">[Bu](../../language-reference/keywords/this.md) anahtar sözcük, Dizin oluşturucuyu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-123">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="ef7d9-124">[Value](../../language-reference/keywords/value.md) anahtar sözcüğü, erişimci tarafından atanan değeri tanımlamak için kullanılır `set` .</span><span class="sxs-lookup"><span data-stu-id="ef7d9-124">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
  
- <span data-ttu-id="ef7d9-125">Dizin oluşturucuların bir tamsayı değeri ile dizinlenmesini gerekmez; Bu, belirli bir arama mekanizmasını nasıl tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-125">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="ef7d9-126">Dizin oluşturucular aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-126">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="ef7d9-127">Dizin oluşturucular birden fazla biçimsel parametreye sahip olabilir, örneğin iki boyutlu bir diziye erişirken.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-127">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a> <span data-ttu-id="ef7d9-128">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="ef7d9-128">Related Sections</span></span>  
  
- [<span data-ttu-id="ef7d9-129">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef7d9-129">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="ef7d9-130">Arabirimlerdeki Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ef7d9-130">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="ef7d9-131">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ef7d9-131">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="ef7d9-132">Erişimci Erişilebilirliğini Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="ef7d9-132">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="ef7d9-133">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ef7d9-133">C# Language Specification</span></span>  

<span data-ttu-id="ef7d9-134">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Dizin oluşturucular](~/_csharplang/spec/classes.md#indexers) .</span><span class="sxs-lookup"><span data-stu-id="ef7d9-134">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ef7d9-135">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-135">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ef7d9-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef7d9-136">See also</span></span>

- [<span data-ttu-id="ef7d9-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ef7d9-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ef7d9-138">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ef7d9-138">Properties</span></span>](../classes-and-structs/properties.md)
