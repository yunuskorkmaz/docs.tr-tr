---
title: Dizin oluşturucular - kullanarak C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 6b129177e6eb916982a27ba76aca517b0642344c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679810"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="5e765-102">Dizin oluşturucular (C# programlama Kılavuzu) kullanma</span><span class="sxs-lookup"><span data-stu-id="5e765-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="5e765-103">Dizin oluşturucular özelliklere oluşturmanıza olanak sağlayan bir söz dizimi kullanışlı bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapı](../../../csharp/language-reference/keywords/struct.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md) istemci uygulamaları bir dizi olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e765-103">Indexers are a syntactic convenience that enable you to create a [class](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md), or [interface](../../../csharp/language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="5e765-104">Dizin Oluşturucular, bir iç toplama veya dizi yalıtılacak birincil amacı olan türlerinde en sık uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5e765-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="5e765-105">Örneğin, bir sınıf olduğunu varsayalım `TempRecord` temsil eden sıcaklık Fahrenhayt bir 24 saatlik dönemde 10 farklı zamanlarda kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="5e765-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="5e765-106">Sınıfı bir dizi içeren `temps` türü `float[]` sıcaklık değerleri depolamak için.</span><span class="sxs-lookup"><span data-stu-id="5e765-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="5e765-107">Bu sınıfta dizin oluşturucu uygulayarak istemcileri olarak sıcaklıklar erişebilir bir `TempRecord` örneği `float temp = tr[4]` yerine olarak `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="5e765-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="5e765-108">Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için sözdizimini basitleştirir; Ayrıca sınıfı ve amacını anlamak diğer geliştiriciler için daha kolay kılar.</span><span class="sxs-lookup"><span data-stu-id="5e765-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="5e765-109">Bir dizin oluşturucu, bir sınıf veya yapı bildirmek için kullanın [bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="5e765-109">To declare an indexer on a class or struct, use the [this](../../../csharp/language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="5e765-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e765-110">Remarks</span></span>

<span data-ttu-id="5e765-111">Bir dizin oluşturucu türüne ve parametrelerinin türü, en az Indexer olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e765-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="5e765-112">Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="5e765-112">For more information about accessibility levels, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="5e765-113">Dizin oluşturucular bir arabirim ile kullanma hakkında daha fazla bilgi için bkz. [arabirim dizin oluşturucuları](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="5e765-113">For more information about how to use indexers with an interface, see [Interface Indexers](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="5e765-114">Bir dizin oluşturucu imzası, sayı ve biçimsel parametrelerinin türleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="5e765-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="5e765-115">Dizin Oluşturucu türü veya biçimsel parametrelerinin adları içermez.</span><span class="sxs-lookup"><span data-stu-id="5e765-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="5e765-116">Aynı sınıf içinde birden fazla dizin oluşturucu bildirirseniz, bunlar farklı imzalarına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e765-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="5e765-117">Bir dizin oluşturucu değeri bir değişkene sınıflandırılmaz; Bu nedenle, bir dizin oluşturucu değer olarak geçirilemez bir [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="5e765-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="5e765-118">Dizin oluşturucunun diğer dillerin kullanabileceği bir ad ile sağlamak için kullanın <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="5e765-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="5e765-119">Bu dizin oluşturucu adı gerekir `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="5e765-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="5e765-120">Ad özniteliği bulunmaması olun `Item` varsayılan adı.</span><span class="sxs-lookup"><span data-stu-id="5e765-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="5e765-121">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="5e765-121">Example 1</span></span>  
  
<span data-ttu-id="5e765-122">Aşağıdaki örnek, bir dizi özel alanı bildirmek gösterilmektedir `temps`ve dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="5e765-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="5e765-123">Dizin oluşturucu örneği doğrudan erişim sağlayan `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="5e765-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="5e765-124">Dizin Oluşturucusu kullanmaya alternatif olarak bir diziyi bildirmek için olan bir [genel](../../../csharp/language-reference/keywords/public.md) üyesi ve üyeleri, erişim `tempRecord.temps[i]`, doğrudan.</span><span class="sxs-lookup"><span data-stu-id="5e765-124">The alternative to using the indexer is to declare the array as a [public](../../../csharp/language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="5e765-125">Bir oluşturucunun erişim, örneğin, içinde çalışırken dikkat bir `Console.Write` deyimi [alma](../../../csharp/language-reference/keywords/get.md) erişimci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e765-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../../csharp/language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="5e765-126">Bu nedenle, hiçbir `get` erişimci yoksa, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="5e765-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="5e765-127">Diğer değerleri kullanarak dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e765-127">Indexing using other values</span></span>

<span data-ttu-id="5e765-128">C#Dizin Oluşturucu parametre türü tamsayı kısıtlamaz.</span><span class="sxs-lookup"><span data-stu-id="5e765-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="5e765-129">Örneğin, bir dizeyi bir dizin oluşturucu ile kullanmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e765-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="5e765-130">Böyle bir dizin oluşturucu, koleksiyondaki dize için arama ve uygun değeri döndüren uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5e765-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="5e765-131">Dize ve tamsayı sürümleri, erişimcileri aşırı yüklenebilir olarak birlikte bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5e765-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="5e765-132">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="5e765-132">Example 2</span></span>  
  
<span data-ttu-id="5e765-133">Aşağıdaki örnek, Haftanın günlerinin ingilizceleridir depolayan bir sınıfı bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e765-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="5e765-134">A `get` erişimci bir dize, bir günün adını alır ve karşılık gelen bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e765-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="5e765-135">Örneğin, "Sunday" 0 değerini döndürür, 1 ve benzeri "Pazartesi" döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e765-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5e765-136">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="5e765-136">Robust programming</span></span>

 <span data-ttu-id="5e765-137">İçinde güvenlik ve dizin oluşturucular güvenilirliğini geliştirilebilir başlıca iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="5e765-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="5e765-138">Herhangi bir türde istemci kodu içinde geçersiz dizin değeri geçirme olasılığını işlemek için hata işleme stratejisi birleştirmek emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e765-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="5e765-139">Bu konunun önceki kısımlarında ilk örnekte TempRecord sınıf girişi için dizin oluşturucuyu iletmeden önce doğrulamak istemci kodu sağlayan bir uzunluk özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e765-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="5e765-140">Hata işleme kod içinde dizin oluşturucunun kendisi de koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e765-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="5e765-141">Kullanıcılar için belge içinde bir dizin oluşturucu erişimci throw özel durumları emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e765-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="5e765-142">Erişilebilirliğini ayarlamak [alma](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) şüphelenilebilir olabildiğince kısıtlayıcı erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="5e765-142">Set the accessibility of the [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="5e765-143">Bu önemlidir `set` özellikle erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="5e765-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="5e765-144">Daha fazla bilgi için [erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="5e765-144">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e765-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e765-145">See also</span></span>

- [<span data-ttu-id="5e765-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e765-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5e765-147">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e765-147">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="5e765-148">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5e765-148">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
