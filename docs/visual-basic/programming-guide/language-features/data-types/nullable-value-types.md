---
title: Boş Değer Atanabilen Değer Türleri
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: 0d259e11a969f4eb7e64626a4adf498db06ece06
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347834"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="551bb-102">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="551bb-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="551bb-103">Bazen belirli koşullarda tanımlı bir değere sahip olmayan bir değer türüyle çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="551bb-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="551bb-104">Örneğin, bir veritabanındaki bir alanın anlamlı bir değere sahip olan ve atanan bir değere sahip olmayan bir değeri ayırt etmek zorunda olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="551bb-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="551bb-105">Değer türleri, normal değerlerini veya null değeri alacak şekilde genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="551bb-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="551bb-106">Böyle bir uzantıya *null atanabilir tür*denir.</span><span class="sxs-lookup"><span data-stu-id="551bb-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="551bb-107">Her null yapılabilir tür, genel <xref:System.Nullable%601> yapısından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="551bb-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="551bb-108">İş ile ilgili etkinlikleri izleyen bir veritabanını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="551bb-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="551bb-109">Aşağıdaki örnek, null yapılabilir `Boolean` türü oluşturur ve bu türde bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="551bb-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="551bb-110">Bildirimi üç şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="551bb-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="551bb-111">Değişken `ridesBusToWork` bir `True`değeri, `False`değeri veya hiçbir değer olamaz.</span><span class="sxs-lookup"><span data-stu-id="551bb-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="551bb-112">İlk varsayılan değeri hiçbir değer değildir, bu durumda bilgilerin bu kişi için henüz alınmamıştır.</span><span class="sxs-lookup"><span data-stu-id="551bb-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="551bb-113">Buna karşılık, `False` bilgilerin alındığı ve kişinin veri yolunun işe yönelik olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="551bb-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="551bb-114">Null yapılabilir türler ile değişkenleri ve özellikleri bildirebilirsiniz ve null yapılabilir bir türdeki öğelerle bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551bb-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="551bb-115">Null yapılabilir türler içeren yordamları parametreler olarak bildirebilirsiniz ve bir `Function` yordamından null yapılabilir bir tür döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551bb-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="551bb-116">Dizi, bir `String`veya sınıf gibi bir başvuru türü üzerinde null yapılabilir bir tür oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="551bb-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="551bb-117">Temel alınan tür bir değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="551bb-117">The underlying type must be a value type.</span></span> <span data-ttu-id="551bb-118">Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="551bb-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="551bb-119">Null yapılabilir bir tür değişkeni kullanma</span><span class="sxs-lookup"><span data-stu-id="551bb-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="551bb-120">Null yapılabilir bir türün en önemli üyeleri, <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="551bb-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="551bb-121">Null yapılabilir bir tür değişkeni için <xref:System.Nullable%601.HasValue%2A>, değişkenin tanımlı bir değer içerip içermediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="551bb-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="551bb-122"><xref:System.Nullable%601.HasValue%2A> `True`, <xref:System.Nullable%601.Value%2A>değerini okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551bb-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="551bb-123"><xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özelliklerinin `ReadOnly` özellikler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="551bb-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="551bb-124">Varsayılan Değerler</span><span class="sxs-lookup"><span data-stu-id="551bb-124">Default Values</span></span>

<span data-ttu-id="551bb-125">Null yapılabilir bir türe sahip bir değişken bildirdiğinizde, <xref:System.Nullable%601.HasValue%2A> özelliğinin varsayılan bir `False`değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="551bb-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="551bb-126">Bu, varsayılan olarak değişkenin temel alınan değer türünün varsayılan değeri yerine tanımlanmış bir değere sahip olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="551bb-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="551bb-127">Aşağıdaki örnekte, `Integer` türünün varsayılan değeri 0 olsa da, `numberOfChildren` başlangıçta tanımlı bir değere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="551bb-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="551bb-128">Null değer, tanımsız veya bilinmeyen bir değeri göstermek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="551bb-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="551bb-129">`numberOfChildren` `Integer`olarak bildirilirse, bilgilerin şu anda kullanılabilir olmadığını gösterebilen bir değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="551bb-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="551bb-130">Değerler depolanıyor</span><span class="sxs-lookup"><span data-stu-id="551bb-130">Storing Values</span></span>

<span data-ttu-id="551bb-131">Bir değeri, genel olarak null yapılabilir bir türdeki bir değişkende veya özellikte depoladığınızda.</span><span class="sxs-lookup"><span data-stu-id="551bb-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="551bb-132">Aşağıdaki örnek, önceki örnekte bildirildiği `numberOfChildren` değişkenine bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="551bb-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="551bb-133">Null yapılabilir bir türün bir değişkeni veya özelliği tanımlanmış bir değer içeriyorsa, kendisine atanmış bir değere sahip olmadığı ilk durumuna dönüşmesine neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551bb-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="551bb-134">Bu, aşağıdaki örnekte gösterildiği gibi değişkeni veya özelliği `Nothing`olarak ayarlayarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551bb-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="551bb-135">`Nothing` Nullable bir tür değişkenine atayabilseniz de, eşittir işaretini kullanarak `Nothing` için test edilemez.</span><span class="sxs-lookup"><span data-stu-id="551bb-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="551bb-136">Eşittir işaretini kullanan karşılaştırma, `someVar = Nothing`her zaman `Nothing`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="551bb-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="551bb-137">Değişkenin <xref:System.Nullable%601.HasValue%2A> özelliğini `False`veya `Is` ya da `IsNot` işlecini kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551bb-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="551bb-138">Değerler alınıyor</span><span class="sxs-lookup"><span data-stu-id="551bb-138">Retrieving Values</span></span>

<span data-ttu-id="551bb-139">Null yapılabilir bir türdeki değişkenin değerini almak için, önce bir değer olduğunu doğrulamak üzere <xref:System.Nullable%601.HasValue%2A> özelliğini sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="551bb-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="551bb-140"><xref:System.Nullable%601.HasValue%2A> `False`olduğunda değeri okumaya çalışırsanız Visual Basic bir <xref:System.InvalidOperationException> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="551bb-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="551bb-141">Aşağıdaki örnek, önceki örneklerin `numberOfChildren` değişkenini okumak için önerilen yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="551bb-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="551bb-142">Null yapılabilir türleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="551bb-142">Comparing Nullable Types</span></span>

<span data-ttu-id="551bb-143">Boolean ifadelerde null yapılabilir `Boolean` değişkenleri kullanıldığında, sonuç `True`, `False`veya `Nothing`olabilir.</span><span class="sxs-lookup"><span data-stu-id="551bb-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="551bb-144">`And` ve `Or`için Truth tablosu aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="551bb-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="551bb-145">`b1` ve `b2` artık üç olası değer içerdiğinden, değerlendirmek için dokuz birleşim vardır.</span><span class="sxs-lookup"><span data-stu-id="551bb-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="551bb-146">B1</span><span class="sxs-lookup"><span data-stu-id="551bb-146">b1</span></span>|<span data-ttu-id="551bb-147">B2</span><span class="sxs-lookup"><span data-stu-id="551bb-147">b2</span></span>|<span data-ttu-id="551bb-148">B1 ve B2</span><span class="sxs-lookup"><span data-stu-id="551bb-148">b1 And b2</span></span>|<span data-ttu-id="551bb-149">B1 veya B2</span><span class="sxs-lookup"><span data-stu-id="551bb-149">b1 Or b2</span></span>|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

<span data-ttu-id="551bb-150">Bir Boole değişkeninin veya ifadesinin değeri `Nothing`, `true` veya `false`değildir.</span><span class="sxs-lookup"><span data-stu-id="551bb-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="551bb-151">Aşağıdaki örneği inceleyin.</span><span class="sxs-lookup"><span data-stu-id="551bb-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="551bb-152">Bu örnekte, `b1 And b2` `Nothing`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="551bb-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="551bb-153">Sonuç olarak, `Else` yan tümcesi her `If` ifadesinde yürütülür ve çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="551bb-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="551bb-154">kısa devre değerlendirmesi kullanan `AndAlso` ve `OrElse`, ilk `Nothing`değerlendirirken ikinci işlenenlerini değerlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="551bb-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="551bb-155">Yayma</span><span class="sxs-lookup"><span data-stu-id="551bb-155">Propagation</span></span>

<span data-ttu-id="551bb-156">Aritmetik, karşılaştırma, kaydırma veya tür işleminin işlenenlerinin bir veya her ikisi null yapılabilir ise, işlemin sonucu da null yapılabilir olur.</span><span class="sxs-lookup"><span data-stu-id="551bb-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="551bb-157">Her iki işlenen de `Nothing`değerler içeriyorsa, işlem null yapılabilir bir tür olmadığı gibi işlenenlerin temel değerlerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="551bb-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="551bb-158">Aşağıdaki örnekte, `compare1` ve `sum1` değişkenleri örtük olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="551bb-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="551bb-159">Fare işaretçisini bunlar üzerinde bekletirseniz, derleyicinin her ikisi için null yapılabilir türler olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="551bb-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="551bb-160">Bir veya iki işlenenin `Nothing`değeri varsa, sonuç `Nothing`olur.</span><span class="sxs-lookup"><span data-stu-id="551bb-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="551bb-161">Null yapılabilir türleri verilerle kullanma</span><span class="sxs-lookup"><span data-stu-id="551bb-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="551bb-162">Veritabanı, null yapılabilir türler kullanmak için en önemli yerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="551bb-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="551bb-163">Tüm veritabanı nesneleri şu anda null yapılabilir türleri desteklememektedir, ancak tasarımcı tarafından oluşturulan tablo bağdaştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="551bb-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="551bb-164">[Nullable türler Için TableAdapter desteği](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="551bb-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="551bb-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="551bb-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="551bb-166">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="551bb-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="551bb-167">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="551bb-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="551bb-168">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="551bb-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="551bb-169">TableAdapter'ları kullanarak veri kümelerini doldurma</span><span class="sxs-lookup"><span data-stu-id="551bb-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="551bb-170">If İşleci</span><span class="sxs-lookup"><span data-stu-id="551bb-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="551bb-171">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="551bb-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="551bb-172">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="551bb-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="551bb-173">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="551bb-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="551bb-174">Nullable değer türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="551bb-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
