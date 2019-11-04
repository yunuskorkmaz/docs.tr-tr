---
title: Dizin oluşturucular C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 02dc8c21b86438c801fb151d9f02a223b60d6197
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423230"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="3e7e2-102">Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3e7e2-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="3e7e2-103">Dizin oluşturucular, bir sınıf veya yapının örneklerinin, tıpkı diziler gibi dizine eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="3e7e2-104">Dizinli değer, açıkça bir tür veya örnek üyesi belirtilmeden ayarlanabilir veya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="3e7e2-105">Dizin oluşturucular, erişimcilerinin parametre kazanması dışında [özelliklere](../classes-and-structs/properties.md) benzer.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="3e7e2-106">Aşağıdaki örnek, değer atamak ve almak için basit [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcisi yöntemleriyle genel bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="3e7e2-107">`Program` sınıfı dizeleri depolamak için bu sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="3e7e2-108">Daha fazla örnek için bkz. [Ilgili bölümler](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="3e7e2-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="3e7e2-109">İfade gövdesi tanımları</span><span class="sxs-lookup"><span data-stu-id="3e7e2-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="3e7e2-110">Bir dizin oluşturucunun Get veya set erişimcisinin bir değer döndüren ya da ayarlayan tek bir deyimden oluşması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="3e7e2-111">İfade-Bodied Üyeler, bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="3e7e2-112">C# 6 ' dan itibaren, aşağıdaki örnekte gösterildiği gibi, salt okunurdur bir Dizin Oluşturucu, bir ifade Bodied üyesi olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="3e7e2-113">`=>` ifade gövdesini tanıtdığına ve `get` anahtar sözcüğünün kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="3e7e2-114">7,0 ile C# başlayarak, hem Get hem de set erişimcisi, ifade Bodied Üyeler olarak uygulanan bir uygulanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="3e7e2-115">Bu durumda, hem `get` hem de `set` anahtar sözcükleri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="3e7e2-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3e7e2-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="3e7e2-117">Dizin Oluşturuculara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e7e2-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="3e7e2-118">Dizin oluşturucular, nesnelerin dizilere benzer bir şekilde dizine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="3e7e2-119">`get` erişimcisi bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="3e7e2-120">`set` erişimcisi bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="3e7e2-121">[Bu](../../language-reference/keywords/this.md) anahtar sözcük, Dizin oluşturucuyu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="3e7e2-122">[Value](../../language-reference/keywords/value.md) anahtar sözcüğü, `set` Indexer tarafından atanan değeri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="3e7e2-123">Dizin oluşturucuların bir tamsayı değeri ile dizinlenmesini gerekmez; Bu, belirli bir arama mekanizmasını nasıl tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="3e7e2-124">Dizin oluşturucular aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="3e7e2-125">Dizin oluşturucular birden fazla biçimsel parametreye sahip olabilir, örneğin iki boyutlu bir diziye erişirken.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="3e7e2-126">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="3e7e2-126">Related Sections</span></span>  
  
- [<span data-ttu-id="3e7e2-127">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="3e7e2-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="3e7e2-128">Arabirimlerdeki Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="3e7e2-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="3e7e2-129">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="3e7e2-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="3e7e2-130">Erişimci Erişilebilirliğini Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="3e7e2-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3e7e2-131">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3e7e2-131">C# Language Specification</span></span>  

<span data-ttu-id="3e7e2-132">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Dizin oluşturucular](~/_csharplang/spec/classes.md#indexers) .</span><span class="sxs-lookup"><span data-stu-id="3e7e2-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="3e7e2-133">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3e7e2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e7e2-134">See also</span></span>

- [<span data-ttu-id="3e7e2-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3e7e2-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3e7e2-136">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="3e7e2-136">Properties</span></span>](../classes-and-structs/properties.md)
