---
title: Dizin Oluşturma - C# Programlama Kılavuzunu Kullanma
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628169"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="a206f-102">Dizin oluşturma (C# Programlama Kılavuzu) kullanma</span><span class="sxs-lookup"><span data-stu-id="a206f-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="a206f-103">Dizin oluşturierler, istemci uygulamalarının bir dizi gibi erişebileceği bir [sınıf,](../../language-reference/keywords/class.md) [yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) oluşturmanıza olanak tanıyan bir sözdizimi kolaylığıdır.</span><span class="sxs-lookup"><span data-stu-id="a206f-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="a206f-104">Dizin leyiciler en sık birincil amacı bir iç koleksiyon veya dizi kapsüllemek için türleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a206f-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="a206f-105">Örneğin, 24 saatlik `TempRecord` bir süre içinde 10 farklı zamanlarda kaydedilen Fahrenhayt sıcaklığını temsil eden bir sınıfolduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a206f-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="a206f-106">Sınıf, sıcaklık `temps` değerlerini `float[]` depolamak için bir dizi tür içerir.</span><span class="sxs-lookup"><span data-stu-id="a206f-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="a206f-107">Bu sınıfta bir dizinleyici uygulayarak, istemciler `TempRecord` gibi `float temp = tr.temps[4]` `float temp = tr[4]` bir örnekte sıcaklıklara erişebilirsiniz .</span><span class="sxs-lookup"><span data-stu-id="a206f-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="a206f-108">Dizinleyici gösterimi yalnızca istemci uygulamaları için sözdizimini basitleştirmekle kalmıyor; aynı zamanda sınıfı ve amacını diğer geliştiricilerin anlaması için daha sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a206f-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="a206f-109">Bir sınıf veya yapı üzerinde bir dizinleyici bildirmek için, aşağıdaki örnekte görüldüğü gibi [bu](../../language-reference/keywords/this.md) anahtar kelimeyi kullanın:</span><span class="sxs-lookup"><span data-stu-id="a206f-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="a206f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a206f-110">Remarks</span></span>

<span data-ttu-id="a206f-111">Dizinleyicinin türü ve parametrelerinin türü en az dizinleyicinin kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a206f-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="a206f-112">Erişilebilirlik düzeyleri hakkında daha fazla bilgi için [erişim değiştiricilere](../../language-reference/keywords/access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a206f-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="a206f-113">Arabirimli dizinleyicilerin nasıl kullanılacağı hakkında daha fazla bilgi için [Interface Indexers'a](./indexers-in-interfaces.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a206f-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="a206f-114">Bir dizinleyicinin imzası, biçimsel parametrelerinin sayısı ve türlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a206f-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="a206f-115">Dizinleyici türünü veya resmi parametrelerin adlarını içermez.</span><span class="sxs-lookup"><span data-stu-id="a206f-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="a206f-116">Aynı sınıfta birden fazla dizinleyici bildirirseniz, farklı imzaları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a206f-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="a206f-117">Bir dizinleyici değeri değişken olarak sınıflandırılmaz; bu nedenle, [bir dizinleyici](../../language-reference/keywords/ref.md) değeri bir ref veya [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçemez.</span><span class="sxs-lookup"><span data-stu-id="a206f-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="a206f-118">Dizin leyiciye diğer dillerin kullanabileceği bir <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>ad sağlamak için aşağıdaki örnekte görüldüğü gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="a206f-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="a206f-119">Bu dizinleyici nin `TheItem`adı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a206f-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="a206f-120">Ad özniteliğinin sağlanmaması `Item` varsayılan adı yapar.</span><span class="sxs-lookup"><span data-stu-id="a206f-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a206f-121">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="a206f-121">Example 1</span></span>  
  
<span data-ttu-id="a206f-122">Aşağıdaki örnek, özel bir dizi alanının `temps`ve dizinleyicinin nasıl bildirilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="a206f-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="a206f-123">Dizinleyici, örneğe `tempRecord[i]`doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a206f-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="a206f-124">Dizinleyici kullanmanın alternatifi, diziyi [genel](../../language-reference/keywords/public.md) üye olarak bildirmek `tempRecord.temps[i]`ve üyelerine doğrudan erişmektir.</span><span class="sxs-lookup"><span data-stu-id="a206f-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="a206f-125">Bir dizin göstericinin erişimi değerlendirildiğinde (örneğin, bir `Console.Write` bildirimde [olsun,](../../language-reference/keywords/get.md) erişim ekive çağrıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a206f-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="a206f-126">Bu nedenle, `get` erişimci yoksa, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="a206f-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="a206f-127">Diğer değerleri kullanarak dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="a206f-127">Indexing using other values</span></span>

<span data-ttu-id="a206f-128">C# dizinleyici parametre türünü sonlu ile sınırlamaz.</span><span class="sxs-lookup"><span data-stu-id="a206f-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="a206f-129">Örneğin, dizinleyicisi olan bir dize kullanmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a206f-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="a206f-130">Böyle bir dizinleyici, koleksiyondaki dizeyi arayarak ve uygun değeri döndürerek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a206f-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="a206f-131">Erişime girenler aşırı yüklenebileceğinden, dize ve tümsek sürümleri birlikte bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a206f-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="a206f-132">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="a206f-132">Example 2</span></span>  
  
<span data-ttu-id="a206f-133">Aşağıdaki örnek, haftanın günlerini depolayan bir sınıf bildirir.</span><span class="sxs-lookup"><span data-stu-id="a206f-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="a206f-134">Bir `get` erişimci bir dize, bir gün adı alır ve karşılık gelen tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a206f-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="a206f-135">Örneğin, "Pazar" 0 döndürür, "Pazartesi" 1 döndürür, ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="a206f-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a206f-136">Sağlam programlama</span><span class="sxs-lookup"><span data-stu-id="a206f-136">Robust programming</span></span>

 <span data-ttu-id="a206f-137">Dizinleyicilerin güvenliği ve güvenilirliğinin geliştirilebildiği iki ana yol vardır:</span><span class="sxs-lookup"><span data-stu-id="a206f-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="a206f-138">Geçersiz bir dizin değerinde istemci kodu geçme olasılığını işlemek için bir tür hata işleme stratejisi dahil emin olun.</span><span class="sxs-lookup"><span data-stu-id="a206f-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="a206f-139">Bu konunun önceki ilk örneğinde, TempRecord sınıfı, istemci kodunun dizinleyiciye geçirmeden önce girişi doğrulamasını sağlayan bir Uzunluk özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a206f-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="a206f-140">Hata işleme kodunu dizinleyicinin içine de koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a206f-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="a206f-141">Dizinleyici erişime aday olduğunuz özel durumları kullanıcılariçin belgelediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a206f-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="a206f-142">[Get'in](../../language-reference/keywords/get.md) erişilebilirliğini ayarlayın ve erişime girenleri makul olduğu kadar kısıtlayıcı olarak [ayarlayın.](../../language-reference/keywords/set.md)</span><span class="sxs-lookup"><span data-stu-id="a206f-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="a206f-143">Bu özellikle `set` erişimci için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a206f-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="a206f-144">Daha fazla bilgi için [bkz.](../classes-and-structs/restricting-accessor-accessibility.md)</span><span class="sxs-lookup"><span data-stu-id="a206f-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a206f-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a206f-145">See also</span></span>

- [<span data-ttu-id="a206f-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a206f-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a206f-147">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a206f-147">Indexers</span></span>](./index.md)
- [<span data-ttu-id="a206f-148">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a206f-148">Properties</span></span>](../classes-and-structs/properties.md)
