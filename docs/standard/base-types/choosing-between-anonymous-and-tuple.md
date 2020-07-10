---
title: Anonim ve demet türleri arasında seçim yapma
description: Anonim türler ve demet türü arasında seçim yapmak için uygun olduğunda bilgi edinin.
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9c186133a639faf187c89d872856d860a20f5a2d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174224"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="a6442-103">Anonim ve demet türleri arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="a6442-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="a6442-104">Uygun türü seçmek, diğer türlere kıyasla kullanılabilirlik, performans ve dengelenmesini kapsar.</span><span class="sxs-lookup"><span data-stu-id="a6442-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="a6442-105">Anonim türler C# 3,0 ' den beri kullanılabilir, ancak genel <xref:System.Tuple%602?displayProperty=nameWithType> türler .NET Framework 4,0 ile tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a6442-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="a6442-106">Daha sonra, adın gösterdiği gibi dil düzeyi desteğiyle yeni seçenekler tanıtıldığından, <xref:System.ValueTuple%602?displayProperty=nameWithType> anonim türlerin esnekliğine sahip bir değer türü sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a6442-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="a6442-107">Bu makalede, diğer bir tür seçmek için uygun olduğunda öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6442-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="a6442-108">Kullanılabilirlik ve işlevsellik</span><span class="sxs-lookup"><span data-stu-id="a6442-108">Usability and functionality</span></span>

<span data-ttu-id="a6442-109">Anonim türler, dil ile tümleşik sorgu (LINQ) ifadeleriyle C# 3,0 ' de tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a6442-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="a6442-110">LINQ ile, geliştiriciler genellikle sorguları üzerinde çalıştıkları nesnelerden birkaç Select özelliği tutan anonim türlere göre proje sonuçları.</span><span class="sxs-lookup"><span data-stu-id="a6442-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="a6442-111">Aşağıdaki örneği bir nesne dizisi örnekleyen <xref:System.DateTime> ve iki özelliği olan anonim bir türde bir şekilde taşıyan bir değer ile yineleyen bir değer düşünün.</span><span class="sxs-lookup"><span data-stu-id="a6442-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="a6442-112">Anonim türler işleç kullanılarak örneklenmiştir [`new`](../../csharp/language-reference/operators/new-operator.md) ve özellik adları ve türleri bildirimden algılanır.</span><span class="sxs-lookup"><span data-stu-id="a6442-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="a6442-113">Aynı derlemede bulunan iki veya daha fazla anonim nesne başlatıcıları aynı sırada olan ve aynı ada ve türe sahip olan bir özellikler sırası belirtse, derleyici nesneleri aynı türdeki örnekler olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a6442-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="a6442-114">Derleyici tarafından oluşturulan tür bilgilerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a6442-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="a6442-115">Önceki C# kod parçacığı, aşağıdaki derleyici tarafından oluşturulan C# sınıfına benzer şekilde, iki özelliği olan anonim bir tür:</span><span class="sxs-lookup"><span data-stu-id="a6442-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="a6442-116">Daha fazla bilgi için bkz. [anonim türler](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a6442-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="a6442-117">Aynı işlevsellik, LINQ sorgularında yansıtıladığında diziler halinde mevcuttur, Özellikler ' i tanımlama grupları ' na seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6442-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="a6442-118">Bu tanımlama grupları, anonim türler gibi sorgu üzerinden akar.</span><span class="sxs-lookup"><span data-stu-id="a6442-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="a6442-119">Şimdi, kullanarak aşağıdaki örneği göz önünde bulundurun `System.Tuple<string, long>` .</span><span class="sxs-lookup"><span data-stu-id="a6442-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="a6442-120">İle, <xref:System.Tuple%602?displayProperty=nameWithType> örneği, ve gibi numaralandırılmış öğe özelliklerini kullanıma sunar `Item1` `Item2` .</span><span class="sxs-lookup"><span data-stu-id="a6442-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="a6442-121">Özellik adı yalnızca sıra sayısını sağladığından, bu özellik adları özellik değerlerinin amacını anlamak daha zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a6442-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="a6442-122">Ayrıca, `System.Tuple` türler başvuru `class` türleridir.</span><span class="sxs-lookup"><span data-stu-id="a6442-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="a6442-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>Ancak, bir değer `struct` türüdür.</span><span class="sxs-lookup"><span data-stu-id="a6442-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="a6442-124">Aşağıdaki C# kod parçacığı, `ValueTuple<string, long>` içinde Project için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6442-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="a6442-125">Bunu yaparken, değişmez bir sözdizimi kullanarak atar.</span><span class="sxs-lookup"><span data-stu-id="a6442-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="a6442-126">Tanımlama grupları hakkında daha fazla bilgi için bkz. [demet türleri (C# Başvurusu)](../../csharp/language-reference/builtin-types/value-tuples.md) veya [tanımlama grupları (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span><span class="sxs-lookup"><span data-stu-id="a6442-126">For more information about tuples, see [Tuple types (C# reference)](../../csharp/language-reference/builtin-types/value-tuples.md) or [Tuples (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span></span>

<span data-ttu-id="a6442-127">Önceki örneklerin hepsi işlevsel olarak eşdeğerdir; ancak kullanılabilirlik ve temel uygulamalarında hafif farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="a6442-127">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="a6442-128">Avantajlar ve Dezavantajlar</span><span class="sxs-lookup"><span data-stu-id="a6442-128">Tradeoffs</span></span>

<span data-ttu-id="a6442-129">Her zaman <xref:System.ValueTuple> <xref:System.Tuple> ve anonim türleri kullanmak isteyebilirsiniz, ancak göz önünde bulundurmanız gereken bir denge vardır.</span><span class="sxs-lookup"><span data-stu-id="a6442-129">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="a6442-130"><xref:System.ValueTuple>Türler değişebilir, ancak <xref:System.Tuple> salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="a6442-130">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="a6442-131">Anonim türler ifade ağaçlarında kullanılabilir, ancak diziler yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6442-131">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="a6442-132">Aşağıdaki tabloda bazı önemli farklılıklara ilişkin bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6442-132">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="a6442-133">Temel farklılıklar</span><span class="sxs-lookup"><span data-stu-id="a6442-133">Key differences</span></span>

| <span data-ttu-id="a6442-134">Ad</span><span class="sxs-lookup"><span data-stu-id="a6442-134">Name</span></span>                     | <span data-ttu-id="a6442-135">Erişim değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="a6442-135">Access modifier</span></span> | <span data-ttu-id="a6442-136">Tür</span><span class="sxs-lookup"><span data-stu-id="a6442-136">Type</span></span>     | <span data-ttu-id="a6442-137">Özel üye adı</span><span class="sxs-lookup"><span data-stu-id="a6442-137">Custom member name</span></span> | <span data-ttu-id="a6442-138">Oluşturmayı kaldırma desteği</span><span class="sxs-lookup"><span data-stu-id="a6442-138">Deconstruction support</span></span> | <span data-ttu-id="a6442-139">İfade ağacı desteği</span><span class="sxs-lookup"><span data-stu-id="a6442-139">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="a6442-140">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a6442-140">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="a6442-141">✔️</span><span class="sxs-lookup"><span data-stu-id="a6442-141">✔️</span></span>                   | ❌                     | <span data-ttu-id="a6442-142">✔️</span><span class="sxs-lookup"><span data-stu-id="a6442-142">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="a6442-143">✔️</span><span class="sxs-lookup"><span data-stu-id="a6442-143">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="a6442-144">✔️</span><span class="sxs-lookup"><span data-stu-id="a6442-144">✔️</span></span>                   | <span data-ttu-id="a6442-145">✔️</span><span class="sxs-lookup"><span data-stu-id="a6442-145">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="a6442-146">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a6442-146">Serialization</span></span>

<span data-ttu-id="a6442-147">Bir tür seçerken dikkat etmeniz gereken önemli bir nokta, serileştirilmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6442-147">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="a6442-148">Serileştirme, bir nesnenin durumunu kalıcı veya taşınan bir biçime dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a6442-148">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="a6442-149">Daha fazla bilgi için bkz. [serileştirme](../../csharp/programming-guide/concepts/serialization/index.md).</span><span class="sxs-lookup"><span data-stu-id="a6442-149">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="a6442-150">Serileştirme önemli olduğunda, `class` `struct` anonim türler veya demet türleri üzerinde bir veya oluşturmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="a6442-150">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="a6442-151">Performans</span><span class="sxs-lookup"><span data-stu-id="a6442-151">Performance</span></span>

<span data-ttu-id="a6442-152">Bu türler arasındaki performans senaryoya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a6442-152">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="a6442-153">Ana etki, ayırma ve kopyalama arasındaki zorunluluğunu getirir içerir.</span><span class="sxs-lookup"><span data-stu-id="a6442-153">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="a6442-154">Çoğu senaryoda, etki küçüktür.</span><span class="sxs-lookup"><span data-stu-id="a6442-154">In most scenarios, the impact is small.</span></span> <span data-ttu-id="a6442-155">Büyük etkileri ortaya çıktığında, kararı bildirmek için ölçümler gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a6442-155">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="a6442-156">Sonuç</span><span class="sxs-lookup"><span data-stu-id="a6442-156">Conclusion</span></span>

<span data-ttu-id="a6442-157">Bir geliştirici olarak tanımlama grupları ve anonim türler arasında seçim yaparak göz önünde bulundurmanız gereken birkaç etken vardır.</span><span class="sxs-lookup"><span data-stu-id="a6442-157">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="a6442-158">Genellikle, [ifade ağaçları](../../csharp/expression-trees.md)ile çalışmadıysanız ve demet söz dizimine rahat bir şekilde sahip olduğunuzda, <xref:System.ValueTuple> özellik adı esnekliği ile bir değer türü sağlayan öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a6442-158">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="a6442-159">İfade ağaçları ile çalışıyorsanız ve özellikleri adlandırmak isterseniz, anonim türler ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a6442-159">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="a6442-160">Aksi takdirde, kullanın <xref:System.Tuple> .</span><span class="sxs-lookup"><span data-stu-id="a6442-160">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6442-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6442-161">See also</span></span>

- [<span data-ttu-id="a6442-162">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a6442-162">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="a6442-163">İfade ağaçları</span><span class="sxs-lookup"><span data-stu-id="a6442-163">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="a6442-164">Demet türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6442-164">Tuple types (C# reference)</span></span>](../../csharp/language-reference/builtin-types/value-tuples.md)
- [<span data-ttu-id="a6442-165">Tanımlama grupları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6442-165">Tuples (Visual Basic)</span></span>](../../visual-basic/programming-guide/language-features/data-types/tuples.md)
- [<span data-ttu-id="a6442-166">Tür tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a6442-166">Type design guidelines</span></span>](../design-guidelines/type.md)
