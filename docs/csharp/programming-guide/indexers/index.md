---
title: Dizinleyiciler - C# Programlama Kılavuzu
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167550"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="2459e-102">Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2459e-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="2459e-103">Dizin leyiciler, bir sınıf veya yapı örneklerinin diziler gibi diziler gibi diziler gibi dizilere eksitre ekilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="2459e-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="2459e-104">Dizinlenen değer, bir tür veya örnek üye açıkça belirtilmeden ayarlanabilir veya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="2459e-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="2459e-105">Dizinleyiciler, erişimcilerin parametreleri alması dışında [özelliklere](../classes-and-structs/properties.md) benzer.</span><span class="sxs-lookup"><span data-stu-id="2459e-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="2459e-106">Aşağıdaki örnek, değerleri atamak ve almak için basit [get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimci yöntemleri ile genel bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2459e-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="2459e-107">Sınıf `Program` dizeleri depolamak için bu sınıfın bir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2459e-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="2459e-108">Daha fazla örnek [için, İlgili Bölümlere](./index.md#BKMK_RelatedSections)bakın.</span><span class="sxs-lookup"><span data-stu-id="2459e-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="2459e-109">İfade Gövde Tanımları</span><span class="sxs-lookup"><span data-stu-id="2459e-109">Expression Body Definitions</span></span>  

<span data-ttu-id="2459e-110">Bir dizin leyicinin erişime sahip olması veya ayarlayan bir değeri döndüren veya ayarlayan tek bir deyimden oluşması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="2459e-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="2459e-111">İfade gövdeli üyeler, bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2459e-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="2459e-112">C# 6 ile başlayarak, aşağıdaki örnekte görüldüğü gibi, salt okunur dizinleyici ifade gövdeli bir üye olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2459e-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="2459e-113">İfade `=>` gövdesini tanıttıve anahtar kelimenin `get` kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2459e-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="2459e-114">C# 7.0 ile başlayarak, hem get hem de set erişimcisi ifade gövdeli üyeler olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2459e-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="2459e-115">Bu durumda, `get` hem `set` anahtar kelimeler hem de anahtar kelimeler kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2459e-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="2459e-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2459e-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="2459e-117">Dizin Oluşturuculara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2459e-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="2459e-118">Dizin leyiciler nesnelerin dizilere benzer şekilde dizilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2459e-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="2459e-119">Bir `get` erişimci bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="2459e-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="2459e-120">Bir `set` erişimci bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="2459e-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="2459e-121">[Bu](../../language-reference/keywords/this.md) anahtar kelime dizinleyicitanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2459e-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="2459e-122">[Değer](../../language-reference/keywords/value.md) anahtar kelimesi `set` dizinleyici tarafından atanan değeri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2459e-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="2459e-123">Dizinleyicilerin bir sonda değeriyle dizine eklenmeleri gerekmez; belirli bir arama mekanizmasını nasıl tanımlayacak size kalmış.</span><span class="sxs-lookup"><span data-stu-id="2459e-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="2459e-124">Dizin leyiciler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2459e-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="2459e-125">Dizin leyicilerin, örneğin iki boyutlu bir diziye erişirken birden fazla resmi parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2459e-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="2459e-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2459e-126">Related Sections</span></span>  
  
- [<span data-ttu-id="2459e-127">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="2459e-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="2459e-128">Arabirimlerdeki Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2459e-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="2459e-129">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="2459e-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="2459e-130">Erişimci Erişilebilirliğini Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="2459e-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2459e-131">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2459e-131">C# Language Specification</span></span>  

<span data-ttu-id="2459e-132">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Dizin](~/_csharplang/spec/classes.md#indexers) leyiciler'e bakın.</span><span class="sxs-lookup"><span data-stu-id="2459e-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2459e-133">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="2459e-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2459e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2459e-134">See also</span></span>

- [<span data-ttu-id="2459e-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2459e-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2459e-136">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2459e-136">Properties</span></span>](../classes-and-structs/properties.md)
