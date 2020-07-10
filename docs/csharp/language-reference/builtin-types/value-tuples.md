---
title: Demet türleri-C# başvurusu
description: 'C# tanımlama bilgileri hakkında bilgi edinin: gevşek ilgili veri öğelerini gruplandırmak için kullanabileceğiniz hafif veri yapıları'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174993"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="ff6e0-103">Demet türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ff6e0-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="ff6e0-104">C# 7,0 ve üzeri sürümlerde, *Tanımlama grupları* özelliği basit bir veri yapısındaki birden çok veri öğesini gruplamak için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="ff6e0-105">Aşağıdaki örnek, bir tanımlama grubu değişkeni bildirme, bunu başlatma ve veri üyelerine erişme işlemlerinin nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

<span data-ttu-id="ff6e0-106">Yukarıdaki örnekte gösterildiği gibi, bir demet türü tanımlamak için, tüm veri üyelerinin ve isteğe bağlı olarak [alan adlarının](#tuple-field-names)türlerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="ff6e0-107">Tanımlama grubu türünde Yöntemler tanımlayamazsınız, ancak aşağıdaki örnekte gösterildiği gibi .NET tarafından sunulan yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="ff6e0-108">C# 7,3 ' den başlayarak demet türleri [eşitlik işleçlerini](../operators/equality-operators.md) `==` ve ' ı destekler `!=` .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="ff6e0-109">Daha fazla bilgi için [demet eşitlik](#tuple-equality) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="ff6e0-110">Demet türleri [değer türleridir](value-types.md); demet öğeleri ortak alanlardır.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="ff6e0-111">Bu, başlıkların *değişebilir* değer türlerini yapar.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="ff6e0-112">Tanımlama grupları özelliği, <xref:System.ValueTuple?displayProperty=nameWithType> <xref:System.ValueTuple%602?displayProperty=nameWithType> .NET Core ve .NET Framework 4,7 ve üzeri sürümlerde bulunan tür ve ilgili genel türleri (örneğin,) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="ff6e0-113">.NET Framework 4.6.2 veya daha önceki bir sürümünü hedefleyen bir projede tanımlama gruplarını kullanmak için, NuGet paketini [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="ff6e0-114">Tanımlama gruplarını rastgele çok sayıda öğe ile tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="ff6e0-115">Tanımlama gruplarının kullanım durumları</span><span class="sxs-lookup"><span data-stu-id="ff6e0-115">Use cases of tuples</span></span>

<span data-ttu-id="ff6e0-116">Tanımlama gruplarının en yaygın kullanım çalışmalarından biri yöntem dönüş türü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="ff6e0-117">Diğer bir deyişle, [ `out` Yöntem parametreleri](../keywords/out-parameter-modifier.md)tanımlamak yerine, aşağıdaki örnekte gösterildiği gibi, yöntemi, kayıt kümesi dönüş türü olarak gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="ff6e0-118">Yukarıdaki örnekte gösterildiği gibi, döndürülen demet örneğiyle doğrudan [çalışabilir veya ayrı](#tuple-assignment-and-deconstruction) değişkenlerde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="ff6e0-119">[Anonim türler](../../programming-guide/classes-and-structs/anonymous-types.md)yerine demet türlerini de kullanabilirsiniz; Örneğin, LINQ sorgularında.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="ff6e0-120">Daha fazla bilgi için bkz. [anonim ve demet türleri arasında seçim yapma](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="ff6e0-121">Genellikle, gevşek ilgili veri öğelerini gruplamak için tanımlama gruplarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="ff6e0-122">Bu, genellikle özel ve iç yardımcı program yöntemlerinde yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="ff6e0-123">Ortak API söz konusu olduğunda, bir [sınıf](../keywords/class.md) veya [Yapı](struct.md) türü tanımlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="ff6e0-124">Demet alan adları</span><span class="sxs-lookup"><span data-stu-id="ff6e0-124">Tuple field names</span></span>

<span data-ttu-id="ff6e0-125">Aşağıdaki örnekte gösterildiği gibi demet başlatma ifadesinde veya bir demet türü tanımında kayıt kümesi alanlarının adlarını açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="ff6e0-126">C# 7,1 ile başlayarak, bir alan adı belirtmezseniz, aşağıdaki örnekte gösterildiği gibi, bir demet başlatma ifadesinde karşılık gelen değişkenin adından çıkarsanolabilir:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="ff6e0-127">Bu, demet projeksiyon başlatıcıları olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="ff6e0-128">Bir değişkenin adı, aşağıdaki durumlarda bir demet alan adı üzerine yansıtılmıyor:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="ff6e0-129">Aday adı, örneğin,, veya gibi bir tanımlama grubu türünün üye adıdır `Item3` `ToString` `Rest` .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="ff6e0-130">Aday adı, başka bir tanımlama grubu alan adının veya açık ya da örtük bir yinelemesidir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="ff6e0-131">Bu durumlarda, bir alanın adını açıkça belirtirsiniz ya da bir alana varsayılan adıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="ff6e0-132">Demet alanlarının varsayılan adları `Item1` ,, vb. ' dir `Item2` `Item3` .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="ff6e0-133">Aşağıdaki örnekte gösterildiği gibi, bir alan adı açıkça veya çıkarsansa bile, bir alanın varsayılan adını her zaman kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="ff6e0-134">[Demet atama](#tuple-assignment-and-deconstruction) ve [tanımlama grubu eşitlik karşılaştırmaları](#tuple-equality) , alan adlarını hesaba almaz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="ff6e0-135">Derleme zamanında, derleyici varsayılan olmayan alan adlarını karşılık gelen varsayılan adlarla değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="ff6e0-136">Sonuç olarak, açıkça belirtilen veya Çıkarsanan alan adları çalışma zamanında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="ff6e0-137">Demet atama ve ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="ff6e0-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="ff6e0-138">C#, aşağıdaki koşulların her ikisini de karşılayan demet türleri arasında atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="ff6e0-139">Her iki demet türü de aynı sayıda öğe içermelidir</span><span class="sxs-lookup"><span data-stu-id="ff6e0-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="ff6e0-140">her demet konumu için, sağ taraftaki demet öğesinin türü, karşılık gelen sol taraftaki demet öğesinin türüne göre veya örtülü olarak dönüştürülebilir</span><span class="sxs-lookup"><span data-stu-id="ff6e0-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="ff6e0-141">Demet öğesi değerleri demet öğelerinin sırasına göre atanır.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="ff6e0-142">Aşağıdaki örnekte gösterildiği gibi, demet alanlarının adları yoksayılır ve atanmaz:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

<span data-ttu-id="ff6e0-143">Ayrıca, `=` farklı değişkenlerde bir demet örneğini bırakmak *deconstruct* için atama işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="ff6e0-144">Bunu aşağıdaki yöntemlerle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="ff6e0-145">Her değişkenin türünü parantez içinde açıkça bildirin:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="ff6e0-146">`var`Örtük olarak yazılmış değişkenleri bildirmek ve derleyicinin türlerini saymasına izin vermek için parantez dışında anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="ff6e0-147">Mevcut değişkenleri kullan:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="ff6e0-148">Başlıkların ve diğer türlerin çıkarılması hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](../../deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="ff6e0-149">Tanımlama grubu eşitliği</span><span class="sxs-lookup"><span data-stu-id="ff6e0-149">Tuple equality</span></span>

<span data-ttu-id="ff6e0-150">C# 7,3 ' den başlayarak demet türleri `==` ve işleçlerini destekler `!=` .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="ff6e0-151">Bu işleçler, sol işlenenin üyelerini, demet öğelerinin sırası takip eden sağ işlenenin ilgili üyeleriyle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="ff6e0-152">Yukarıdaki örnekte gösterildiği gibi, `==` ve işlemleri de `!=` Hesap tanımlama grubu alan adlarını almaz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="ff6e0-153">İki tanımlama grubu, aşağıdaki koşulların her ikisi de karşılanmadığı zaman karşılaştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="ff6e0-154">Her iki tanımlama grubu aynı sayıda öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="ff6e0-155">Örneğin, `t1 != t2` `t1` ve `t2` farklı sayıda öğe varsa derleme yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="ff6e0-156">Her demet konumu için, sol taraftaki ve sağ taraftaki demet işlenenlerinden karşılık gelen öğeler `==` ve `!=` işleçleriyle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="ff6e0-157">Örneğin, `(1, (2, 3)) == ((1, 2), 3)` ile karşılaştırılabilir olmadığı için derleme yapmaz `1` `(1, 2)` .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="ff6e0-158">`==`Ve `!=` işleçleri, tanımlama gruplarını kısa devre bir şekilde karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="ff6e0-159">Diğer bir deyişle, bir işlem eşit olmayan bir öğe çifti karşıladığında veya tanımlama gruplarının uçlarına ulaştığında duraklar.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="ff6e0-160">Ancak, herhangi bir karşılaştırmaya başlamadan önce, aşağıdaki örnekte gösterildiği gibi *Tüm* demet öğeleri değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="ff6e0-161">Out parametreleri olarak tanımlama grubu</span><span class="sxs-lookup"><span data-stu-id="ff6e0-161">Tuples as out parameters</span></span>

<span data-ttu-id="ff6e0-162">Genellikle, [ `out` parametreleri](../keywords/out-parameter-modifier.md) olan bir yöntemi, bir tanımlama grubu döndüren bir yönteme yeniden düzenlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="ff6e0-163">Ancak, bir `out` parametrenin demet türünde olabilecek durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="ff6e0-164">Aşağıdaki örnek, tanımlama grupları ile parametre olarak nasıl çalışalınacağını gösterir `out` :</span><span class="sxs-lookup"><span data-stu-id="ff6e0-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="ff6e0-165">Ve başlıkları`System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="ff6e0-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="ff6e0-166">Türlerine göre desteklenen C# tanımlama grupları <xref:System.ValueTuple?displayProperty=nameWithType> , türlerle temsil edilen tanımlama tiplerinden farklıdır <xref:System.Tuple?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="ff6e0-167">Ana farklılıklar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-167">The main differences are as follows:</span></span>

- <span data-ttu-id="ff6e0-168">`ValueTuple`türler [değer türlerdir](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="ff6e0-169">`Tuple`türler [başvuru türleridir](../keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="ff6e0-170">`ValueTuple`türler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="ff6e0-171">`Tuple`türler sabittir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="ff6e0-172">Türlerin veri üyeleri `ValueTuple` alanlardır.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="ff6e0-173">Türlerin veri üyeleri `Tuple` özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ff6e0-174">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ff6e0-174">C# language specification</span></span>

<span data-ttu-id="ff6e0-175">Daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="ff6e0-176">Tanımlama grubu adlarını (yani, aka. Tuple projeksiyon başlatıcıları) çıkar</span><span class="sxs-lookup"><span data-stu-id="ff6e0-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="ff6e0-177">`==` `!=` Tanımlama grubu türleri için ve desteği</span><span class="sxs-lookup"><span data-stu-id="ff6e0-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="ff6e0-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-178">See also</span></span>

- [<span data-ttu-id="ff6e0-179">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ff6e0-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ff6e0-180">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="ff6e0-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="ff6e0-181">Anonim ve demet türleri arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="ff6e0-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
