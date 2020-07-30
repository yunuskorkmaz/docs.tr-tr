---
title: Dizin oluşturucular kullanma-C# Programlama Kılavuzu
description: C# ' de bir sınıf, yapı veya arabirim için Dizin Oluşturucu tanımlamayı ve kullanmayı öğrenin. Bu makale örnek kod içerir.
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: a8a9e05c1d2e44841177a924c6ff51c6c9e6a05a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301872"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="609a9-104">Dizin oluşturucular kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="609a9-104">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="609a9-105">Dizin oluşturucular, istemci uygulamaların dizi olarak erişebileceği bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) oluşturmanıza imkan tanıyan sözdizimsel bir kolaylığıdır.</span><span class="sxs-lookup"><span data-stu-id="609a9-105">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access as an array.</span></span> <span data-ttu-id="609a9-106">Derleyici bir `Item` Özellik (veya varsa alternatif olarak adlandırılmış bir özellik) oluşturur <xref:System.Runtime.CompilerServices.IndexerNameAttribute> ve uygun erişimci yöntemleri olur.</span><span class="sxs-lookup"><span data-stu-id="609a9-106">The compiler will generate an `Item` property (or an alternatively named property if <xref:System.Runtime.CompilerServices.IndexerNameAttribute> is present), and the appropriate accessor methods.</span></span> <span data-ttu-id="609a9-107">Dizin oluşturucular en sık, birincil amacı bir iç koleksiyonu veya diziyi kapsüllemek olan türlerde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="609a9-107">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="609a9-108">Örneğin, `TempRecord` 24 saatlik bir dönemde 10 farklı zamanda kaydedildiği gibi Fahrenhayt 'teki sıcaklığı temsil eden bir sınıfınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="609a9-108">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period.</span></span> <span data-ttu-id="609a9-109">Sınıfı, `temps` `float[]` sıcaklık değerlerini depolamak için türünde bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="609a9-109">The class contains a `temps` array of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="609a9-110">Bu sınıfta bir Dizin Oluşturucu uygulayarak istemciler, gibi bir örnekteki sıcakya farklı şekilde erişebilir `TempRecord` `float temp = tempRecord[4]` `float temp = tempRecord.temps[4]` .</span><span class="sxs-lookup"><span data-stu-id="609a9-110">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tempRecord[4]` instead of as `float temp = tempRecord.temps[4]`.</span></span> <span data-ttu-id="609a9-111">Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için söz dizimini basitleştirir; Ayrıca, diğer geliştiricilerin anlayabilmesi için sınıfı ve amacını daha sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="609a9-111">The indexer notation not only simplifies the syntax for client applications; it also makes the class, and its purpose more intuitive for other developers to understand.</span></span>

<span data-ttu-id="609a9-112">Bir sınıf veya yapı biriminde bir Dizin Oluşturucu bildirmek için aşağıdaki örnekte gösterildiği gibi [this](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="609a9-112">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> <span data-ttu-id="609a9-113">Bir dizin oluşturucunun bildirilmesi, otomatik olarak nesne üzerinde adlı bir özellik oluşturur `Item` .</span><span class="sxs-lookup"><span data-stu-id="609a9-113">Declaring an indexer will automatically generate a property named `Item` on the object.</span></span> <span data-ttu-id="609a9-114">`Item`Özelliğe, örnek [üye erişim ifadesinden](../../language-reference/operators/member-access-operators.md#member-access-expression-)doğrudan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="609a9-114">The `Item` property is not directly accessible from the instance [member access expression](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="609a9-115">Ayrıca, kendi `Item` özelliklerinizi bir dizin oluşturucuya sahip bir nesneye eklerseniz, bir [CS0102 derleyici hatası](../../misc/cs0102.md)alırsınız.</span><span class="sxs-lookup"><span data-stu-id="609a9-115">Additionally, if you add your own `Item` property to an object with an indexer, you'll get a [CS0102 compiler error](../../misc/cs0102.md).</span></span> <span data-ttu-id="609a9-116">Bu hatayı önlemek için, <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Dizin oluşturucuyu aşağıda açıklandığı gibi yeniden adlandır ' ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="609a9-116">To avoid this error, use the <xref:System.Runtime.CompilerServices.IndexerNameAttribute> rename the indexer as detailed below.</span></span>

## <a name="remarks"></a><span data-ttu-id="609a9-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="609a9-117">Remarks</span></span>

<span data-ttu-id="609a9-118">Bir dizin oluşturucunun türü ve parametrelerinin türü en az dizin oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="609a9-118">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="609a9-119">Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="609a9-119">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>

<span data-ttu-id="609a9-120">Arabirim ile Dizin oluşturucular kullanma hakkında daha fazla bilgi için bkz. [arabirim dizin oluşturucular](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="609a9-120">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>

<span data-ttu-id="609a9-121">Bir dizin oluşturucunun imzası, biçimsel parametrelerinin sayısı ve türlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="609a9-121">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="609a9-122">Dizin Oluşturucu türü veya biçimsel parametrelerin adlarını içermez.</span><span class="sxs-lookup"><span data-stu-id="609a9-122">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="609a9-123">Aynı sınıfta birden fazla Dizin Oluşturucu bildirirseniz, bunların farklı imzaları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="609a9-123">If you declare more than one indexer in the same class, they must have different signatures.</span></span>

<span data-ttu-id="609a9-124">Dizin Oluşturucu değeri bir değişken olarak sınıflandırılmıyor; Bu nedenle, Dizin Oluşturucu değeri bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="609a9-124">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="609a9-125">Dizin oluşturucuyu diğer dillerin kullanabileceği bir adla sağlamak için, <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="609a9-125">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

<span data-ttu-id="609a9-126">Dizin `TheItem` Oluşturucu adı özniteliği tarafından geçersiz kılındığından, bu dizin oluşturucunun adı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="609a9-126">This indexer will have the name `TheItem`, as it is overridden by the indexer name attribute.</span></span> <span data-ttu-id="609a9-127">Varsayılan olarak, dizin oluşturucu adı `Item` .</span><span class="sxs-lookup"><span data-stu-id="609a9-127">By default, the indexer name is `Item`.</span></span>

## <a name="example-1"></a><span data-ttu-id="609a9-128">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="609a9-128">Example 1</span></span>

<span data-ttu-id="609a9-129">Aşağıdaki örnek, bir özel dizi alanının, `temps` ve bir dizin oluşturucunun nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="609a9-129">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="609a9-130">Dizin Oluşturucu örneğe doğrudan erişim sağlar `tempRecord[i]` .</span><span class="sxs-lookup"><span data-stu-id="609a9-130">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="609a9-131">Dizin oluşturucuyu kullanmanın alternatifi, diziyi [ortak](../../language-reference/keywords/public.md) bir üye olarak bildirmeli ve üyelerine doğrudan erişim sağlar `tempRecord.temps[i]` .</span><span class="sxs-lookup"><span data-stu-id="609a9-131">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

<span data-ttu-id="609a9-132">Bir dizin oluşturucunun erişim değerlendirildiği zaman, örneğin bir `Console.Write` ifadede, [Get](../../language-reference/keywords/get.md) erişimcisinin çağrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="609a9-132">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="609a9-133">Bu nedenle, `get` bir erişimci yoksa, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="609a9-133">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a><span data-ttu-id="609a9-134">Diğer değerleri kullanarak dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="609a9-134">Indexing using other values</span></span>

<span data-ttu-id="609a9-135">C#, dizin oluşturucu parametre türünü tamsayı olarak sınırlamaz.</span><span class="sxs-lookup"><span data-stu-id="609a9-135">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="609a9-136">Örneğin, bir Dizin Oluşturucu ile dize kullanmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="609a9-136">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="609a9-137">Bu tür bir Dizin Oluşturucu koleksiyondaki dizeyi arayarak ve uygun değeri döndürerek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="609a9-137">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="609a9-138">Erişimciler aşırı yüklenmiş olabilir, dize ve tamsayı sürümleri birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="609a9-138">As accessors can be overloaded, the string and integer versions can coexist.</span></span>

## <a name="example-2"></a><span data-ttu-id="609a9-139">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="609a9-139">Example 2</span></span>

<span data-ttu-id="609a9-140">Aşağıdaki örnek, haftanın günlerini depolayan bir sınıf bildirir.</span><span class="sxs-lookup"><span data-stu-id="609a9-140">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="609a9-141">`get`Erişimci bir dize, bir günün adı alır ve karşılık gelen tamsayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="609a9-141">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="609a9-142">Örneğin, "Pazar" 0, "Pazartesi" 1 döndürür ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="609a9-142">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a><span data-ttu-id="609a9-143">Tüketim örneği 2</span><span class="sxs-lookup"><span data-stu-id="609a9-143">Consuming example 2</span></span>

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a><span data-ttu-id="609a9-144">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="609a9-144">Example 3</span></span>

<span data-ttu-id="609a9-145">Aşağıdaki örnek, sabit listesini kullanarak haftanın günlerini depolayan bir sınıf bildirir <xref:System.DayOfWeek?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="609a9-145">The following example declares a class that stores the days of the week using the <xref:System.DayOfWeek?displayProperty=fullName> enum.</span></span> <span data-ttu-id="609a9-146">`get`Erişimci bir `DayOfWeek` günün değerini alır ve karşılık gelen tamsayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="609a9-146">A `get` accessor takes a `DayOfWeek`, the value of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="609a9-147">Örneğin, `DayOfWeek.Sunday` 0 döndürür, `DayOfWeek.Monday` 1 döndürür ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="609a9-147">For example, `DayOfWeek.Sunday` returns 0, `DayOfWeek.Monday` returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a><span data-ttu-id="609a9-148">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="609a9-148">Consuming example 3</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a><span data-ttu-id="609a9-149">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="609a9-149">Robust programming</span></span>

<span data-ttu-id="609a9-150">Dizin oluşturucularının güvenliğinin ve güvenilirliğinin iyileşmesi için kullanabileceğiniz iki ana yol vardır:</span><span class="sxs-lookup"><span data-stu-id="609a9-150">There are two main ways in which the security and reliability of indexers can be improved:</span></span>

- <span data-ttu-id="609a9-151">İstemci kodunun geçersiz bir dizin değeri geçirme olasılığını işlemek için bir tür hata işleme stratejisi eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="609a9-151">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="609a9-152">Bu konunun önceki kısımlarında yer alan ilk örnekte, TempRecord sınıfı, istemci kodun dizin oluşturucuya geçirmeden önce girişi doğrulamasını sağlayan bir length özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="609a9-152">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="609a9-153">Hata işleme kodunu dizin oluşturucunun içine de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609a9-153">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="609a9-154">Bir Dizin Oluşturucu erişimcisinde oluşturduğunuz tüm özel durumları kullanıcılara belgelediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="609a9-154">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>

- <span data-ttu-id="609a9-155">[Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcilerinin erişilebilirliğini makul olacak şekilde kısıtlayıcı olarak belirleyin.</span><span class="sxs-lookup"><span data-stu-id="609a9-155">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="609a9-156">Bu, `set` özellikle erişimcinin açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="609a9-156">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="609a9-157">Daha fazla bilgi için bkz. [erişimci erişilebilirliğini kısıtlama](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="609a9-157">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="609a9-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609a9-158">See also</span></span>

- [<span data-ttu-id="609a9-159">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="609a9-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="609a9-160">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="609a9-160">Indexers</span></span>](./index.md)
- [<span data-ttu-id="609a9-161">Özellikler</span><span class="sxs-lookup"><span data-stu-id="609a9-161">Properties</span></span>](../classes-and-structs/properties.md)
