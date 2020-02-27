---
title: Dizin oluşturucular kullanma C# -Programlama Kılavuzu
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628169"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="7c5c4-102">Dizin oluşturucular kullanmaC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7c5c4-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="7c5c4-103">Dizin oluşturucular, istemci uygulamaların yalnızca bir dizi olarak erişebileceği bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) oluşturmanıza imkan tanıyan sözdizimsel bir kolaydır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="7c5c4-104">Dizin oluşturucular en sık, birincil amacı bir iç koleksiyonu veya diziyi kapsüllemek olan türlerde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="7c5c4-105">Örneğin, 24 saatlik bir dönemde 10 farklı zamanda kaydedilen Fahrenhayt 'teki sıcaklığı temsil eden bir sınıf `TempRecord` olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="7c5c4-106">Sınıfı, sıcaklık değerlerini depolamak için `float[]` türünde bir dizi `temps` içerir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="7c5c4-107">Bu sınıfta bir Dizin Oluşturucu uygulayarak, istemciler, bir `TempRecord` örneğindeki sıcaklıkların `float temp = tr.temps[4]`yerine `float temp = tr[4]` olarak erişebileceği.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="7c5c4-108">Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için söz dizimini basitleştirir; Ayrıca, diğer geliştiricilerin anlayabilmesi için sınıfı ve amacını daha sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="7c5c4-109">Bir sınıf veya yapı biriminde bir Dizin Oluşturucu bildirmek için aşağıdaki örnekte gösterildiği gibi [this](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c5c4-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="7c5c4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c5c4-110">Remarks</span></span>

<span data-ttu-id="7c5c4-111">Bir dizin oluşturucunun türü ve parametrelerinin türü en az dizin oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="7c5c4-112">Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7c5c4-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="7c5c4-113">Arabirim ile Dizin oluşturucular kullanma hakkında daha fazla bilgi için bkz. [arabirim dizin oluşturucular](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="7c5c4-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="7c5c4-114">Bir dizin oluşturucunun imzası, biçimsel parametrelerinin sayısı ve türlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="7c5c4-115">Dizin Oluşturucu türü veya biçimsel parametrelerin adlarını içermez.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="7c5c4-116">Aynı sınıfta birden fazla Dizin Oluşturucu bildirirseniz, bunların farklı imzaları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="7c5c4-117">Dizin Oluşturucu değeri bir değişken olarak sınıflandırılmıyor; Bu nedenle, Dizin Oluşturucu değeri bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="7c5c4-118">Dizin oluşturucuyu diğer dillerin kullanabileceği bir adla sağlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c5c4-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="7c5c4-119">Bu dizin oluşturucunun adı `TheItem`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="7c5c4-120">Ad özniteliği sağlanmaması varsayılan adı `Item` hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="7c5c4-121">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="7c5c4-121">Example 1</span></span>  
  
<span data-ttu-id="7c5c4-122">Aşağıdaki örnek, bir özel dizi alanının, `temps`ve bir dizin oluşturucunun nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="7c5c4-123">Dizin Oluşturucu, `tempRecord[i]`örneğine doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="7c5c4-124">Dizin oluşturucuyu kullanmanın alternatifi diziyi [ortak](../../language-reference/keywords/public.md) bir üye olarak bildirmeli ve üyelerine `tempRecord.temps[i]`doğrudan.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="7c5c4-125">Bir dizin oluşturucunun erişimi değerlendirildiğinde, örneğin, bir `Console.Write` bildiriminde, [Get](../../language-reference/keywords/get.md) erişimcisinin çağrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="7c5c4-126">Bu nedenle `get` erişimci yoksa, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="7c5c4-127">Diğer değerleri kullanarak dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c5c4-127">Indexing using other values</span></span>

<span data-ttu-id="7c5c4-128">C#Dizin Oluşturucu parametre türü tamsayı olarak sınırlandırmaz.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="7c5c4-129">Örneğin, bir Dizin Oluşturucu ile dize kullanmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="7c5c4-130">Bu tür bir Dizin Oluşturucu koleksiyondaki dizeyi arayarak ve uygun değeri döndürerek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="7c5c4-131">Erişimciler aşırı yüklenmiş olabilir, dize ve tamsayı sürümleri birlikte bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="7c5c4-132">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="7c5c4-132">Example 2</span></span>  
  
<span data-ttu-id="7c5c4-133">Aşağıdaki örnek, haftanın günlerini depolayan bir sınıf bildirir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="7c5c4-134">`get` erişimcisi bir dize, bir günün adı alır ve karşılık gelen tamsayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="7c5c4-135">Örneğin, "Pazar" 0, "Pazartesi" 1 döndürür ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7c5c4-136">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="7c5c4-136">Robust programming</span></span>

 <span data-ttu-id="7c5c4-137">Dizin oluşturucularının güvenliğinin ve güvenilirliğinin iyileşmesi için kullanabileceğiniz iki ana yol vardır:</span><span class="sxs-lookup"><span data-stu-id="7c5c4-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="7c5c4-138">İstemci kodunun geçersiz bir dizin değeri geçirme olasılığını işlemek için bir tür hata işleme stratejisi eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="7c5c4-139">Bu konunun önceki kısımlarında yer alan ilk örnekte, TempRecord sınıfı, istemci kodun dizin oluşturucuya geçirmeden önce girişi doğrulamasını sağlayan bir length özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="7c5c4-140">Hata işleme kodunu dizin oluşturucunun içine de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="7c5c4-141">Bir Dizin Oluşturucu erişimcisinde oluşturduğunuz tüm özel durumları kullanıcılara belgelediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="7c5c4-142">[Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcilerinin erişilebilirliğini makul olacak şekilde kısıtlayıcı olarak belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="7c5c4-143">Bu, özellikle `set` erişimci için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="7c5c4-144">Daha fazla bilgi için bkz. [erişimci erişilebilirliğini kısıtlama](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="7c5c4-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5c4-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-145">See also</span></span>

- [<span data-ttu-id="7c5c4-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7c5c4-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c5c4-147">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7c5c4-147">Indexers</span></span>](./index.md)
- [<span data-ttu-id="7c5c4-148">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7c5c4-148">Properties</span></span>](../classes-and-structs/properties.md)
