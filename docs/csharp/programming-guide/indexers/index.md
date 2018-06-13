---
title: Dizin Oluşturucular (C# Programlama Kılavuzu)
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: acc82ca370a71a0469fc543d042da9c279d69fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334226"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="8024f-102">Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8024f-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="8024f-103">Dizin oluşturucular sınıfta veya yapı yalnızca diziler gibi dizine örneklerini izin verin.</span><span class="sxs-lookup"><span data-stu-id="8024f-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="8024f-104">Dizinli değer ayarlayın veya açıkça türü veya örnek bir üye belirtilmeden alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="8024f-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="8024f-105">Dizin oluşturucular benzer [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) kendi erişimciler parametre almaz ancak bu.</span><span class="sxs-lookup"><span data-stu-id="8024f-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="8024f-106">Aşağıdaki örnekte basit ile genel bir sınıf tanımlar [almak](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) atamak ve değerleri almak için erişimci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8024f-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="8024f-107">`Program` Sınıfı, dizeleri depolamak için bu sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8024f-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="8024f-108">Daha fazla örnek için bkz: [ilgili bölümler](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="8024f-108">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="8024f-109">İfade gövdesi tanımları</span><span class="sxs-lookup"><span data-stu-id="8024f-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="8024f-110">Bir oluşturucunun get veya set erişimcisi döndürür veya bir değer ayarlar tek bir deyimde oluşması için yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="8024f-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="8024f-111">İfade bodied üyeleri bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8024f-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="8024f-112">C# 6 ile başlayarak, bir salt okunur dizin oluşturucu aşağıdaki örnekte gösterildiği gibi bir ifade bodied üye olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8024f-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="8024f-113">Unutmayın `=>` ifade gövde ve tanıtır `get` anahtar sözcüğü kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8024f-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="8024f-114">C# 7.0, hem get'ile başlayan ve set erişimcisi uygulanan bir ifade bodied üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8024f-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="8024f-115">Bu durumda, her ikisi de `get` ve `set` anahtar sözcükleri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8024f-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="8024f-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8024f-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="8024f-117">Dizin Oluşturuculara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8024f-117">Indexers Overview</span></span>  
  
-   <span data-ttu-id="8024f-118">Dizin oluşturucular dizilerine benzer bir şekilde dizine nesneleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8024f-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="8024f-119">A `get` erişimci değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8024f-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="8024f-120">A `set` erişimci değeri atar.</span><span class="sxs-lookup"><span data-stu-id="8024f-120">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="8024f-121">[Bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü dizin oluşturucu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8024f-121">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="8024f-122">[Değeri](../../../csharp/language-reference/keywords/value.md) tarafından atanan değer tanımlamak için kullanılan anahtar sözcüğü `set` dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="8024f-122">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="8024f-123">Dizin oluşturucular tarafından bir tamsayı değeri sıralanması gerekmez; Bu size, belirli arama mekanizması tanımlamak nasıl bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8024f-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="8024f-124">Dizin oluşturucular aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8024f-124">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="8024f-125">Dizin oluşturucular birden fazla biçimsel parametresi, örneğin, iki boyutlu bir dizi erişirken olabilir.</span><span class="sxs-lookup"><span data-stu-id="8024f-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <a name="BKMK_RelatedSections"></a> <span data-ttu-id="8024f-126">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="8024f-126">Related Sections</span></span>  
  
-   [<span data-ttu-id="8024f-127">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="8024f-127">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="8024f-128">Arabirimlerdeki Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8024f-128">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="8024f-129">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="8024f-129">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="8024f-130">Erişimci Erişilebilirliğini Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8024f-130">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="8024f-131">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8024f-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8024f-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8024f-132">See Also</span></span>  
 [<span data-ttu-id="8024f-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8024f-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8024f-134">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8024f-134">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
