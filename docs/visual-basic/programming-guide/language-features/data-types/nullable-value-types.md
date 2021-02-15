---
description: 'Daha fazla bilgi için: Nullable değer türleri (Visual Basic)'
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
ms.openlocfilehash: acc91d98a3ed288a9bf0bcf6abbd3d8a516bd699
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483891"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="be0a4-103">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be0a4-103">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="be0a4-104">Bazen belirli koşullarda tanımlı bir değere sahip olmayan bir değer türüyle çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="be0a4-104">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="be0a4-105">Örneğin, bir veritabanındaki bir alanın anlamlı bir değere sahip olan ve atanan bir değere sahip olmayan bir değeri ayırt etmek zorunda olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-105">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="be0a4-106">Değer türleri, normal değerlerini veya null değeri alacak şekilde genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-106">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="be0a4-107">Böyle bir uzantıya *null atanabilir tür* denir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-107">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="be0a4-108">Her null yapılabilir değer türü genel <xref:System.Nullable%601> yapıdan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be0a4-108">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="be0a4-109">İş ile ilgili etkinlikleri izleyen bir veritabanını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="be0a4-109">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="be0a4-110">Aşağıdaki örnek, null yapılabilir bir `Boolean` tür oluşturur ve bu türde bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-110">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="be0a4-111">Bildirimi üç şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="be0a4-111">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="be0a4-112">Değişken, bir değeri `ridesBusToWork` `True` , değeri veya herhangi bir değer içerebilir `False` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-112">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="be0a4-113">İlk varsayılan değeri hiçbir değer değildir, bu durumda bilgilerin bu kişi için henüz alınmamıştır.</span><span class="sxs-lookup"><span data-stu-id="be0a4-113">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="be0a4-114">Buna karşılık, `False` bilgilerin alındığı ve kişinin veri yolunun işe yönelik olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-114">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="be0a4-115">Null yapılabilir değer türleriyle değişkenleri ve özellikleri bildirebilirsiniz ve null olabilen bir değer türünün öğeleriyle bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0a4-115">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="be0a4-116">Null yapılabilir değer türleri olan yordamları parametreler olarak bildirebilirsiniz ve bir yordamdan null yapılabilir bir değer türü döndürebilirsiniz `Function` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-116">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="be0a4-117">Dizi, a veya sınıf gibi bir başvuru türü üzerinde null yapılabilir bir tür oluşturamazsınız `String` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-117">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="be0a4-118">Temel alınan tür bir değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be0a4-118">The underlying type must be a value type.</span></span> <span data-ttu-id="be0a4-119">Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="be0a4-119">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="be0a4-120">Null yapılabilir bir tür değişkeni kullanma</span><span class="sxs-lookup"><span data-stu-id="be0a4-120">Using a Nullable Type Variable</span></span>

<span data-ttu-id="be0a4-121">Null olabilen bir değer türünün en önemli üyeleri, <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-121">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="be0a4-122">Null yapılabilir değer türünde bir değişken için, <xref:System.Nullable%601.HasValue%2A> değişkenin tanımlı bir değer içerip içermediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="be0a4-122">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="be0a4-123"><xref:System.Nullable%601.HasValue%2A>İse `True` , öğesinden değeri okuyabilirsiniz <xref:System.Nullable%601.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="be0a4-123">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="be0a4-124">Hem hem de <xref:System.Nullable%601.HasValue%2A> özelliklerinin olduğunu unutmayın <xref:System.Nullable%601.Value%2A> `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-124">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="be0a4-125">Varsayılan Değerler</span><span class="sxs-lookup"><span data-stu-id="be0a4-125">Default Values</span></span>

<span data-ttu-id="be0a4-126">Null yapılabilir değer türüne sahip bir değişken bildirdiğinizde, <xref:System.Nullable%601.HasValue%2A> özelliği varsayılan değerine sahiptir `False` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-126">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="be0a4-127">Bu, varsayılan olarak değişkenin temel alınan değer türünün varsayılan değeri yerine tanımlanmış bir değere sahip olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-127">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="be0a4-128">Aşağıdaki örnekte, `numberOfChildren` türünün varsayılan değeri 0 olsa bile başlangıçta tanımlı bir değere sahip değildir `Integer` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-128">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="be0a4-129">Null değer, tanımsız veya bilinmeyen bir değeri göstermek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="be0a4-129">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="be0a4-130">`numberOfChildren`Olarak bildirilirse `Integer` , bilgilerin şu anda kullanılabilir olmadığını gösterebilen bir değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="be0a4-130">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="be0a4-131">Değerler depolanıyor</span><span class="sxs-lookup"><span data-stu-id="be0a4-131">Storing Values</span></span>

<span data-ttu-id="be0a4-132">Bir değeri, null olabilen bir değer türünün bir değişkeninde veya özelliğinde normal şekilde depoladığınızda.</span><span class="sxs-lookup"><span data-stu-id="be0a4-132">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="be0a4-133">Aşağıdaki örnek, önceki örnekte belirtilen değişkenine bir değer atar `numberOfChildren` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-133">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="be0a4-134">Null yapılabilir bir değer türünün bir değişkeni veya özelliği tanımlanmış bir değer içeriyorsa, kendisine atanmış bir değere sahip olmadığı ilk durumuna dönüşmesine neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0a4-134">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="be0a4-135">Bunu, `Nothing` Aşağıdaki örnekte gösterildiği gibi değişkeni veya özelliğini olarak ayarlayarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0a4-135">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="be0a4-136">`Nothing`Null olabilen bir değer türünün değişkenine atayabilirsiniz, ancak `Nothing` eşittir işaretini kullanarak için test edilemez.</span><span class="sxs-lookup"><span data-stu-id="be0a4-136">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="be0a4-137">Eşittir işaretini kullanan karşılaştırma, `someVar = Nothing` her zaman olarak değerlendirilir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-137">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="be0a4-138"><xref:System.Nullable%601.HasValue%2A>Veya işlecini kullanarak değişkeninin özelliğini test edebilir `False` veya test edebilirsiniz `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-138">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="be0a4-139">Değerler alınıyor</span><span class="sxs-lookup"><span data-stu-id="be0a4-139">Retrieving Values</span></span>

<span data-ttu-id="be0a4-140">Null olabilen değer türündeki bir değişkenin değerini almak için, <xref:System.Nullable%601.HasValue%2A> bir değeri olduğunu doğrulamak üzere öncelikle özelliğini sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="be0a4-140">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="be0a4-141">Olduğunda değeri okumaya çalışırsanız <xref:System.Nullable%601.HasValue%2A> `False` , Visual Basic bir <xref:System.InvalidOperationException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be0a4-141">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="be0a4-142">Aşağıdaki örnek, önceki örneklerin değişkenini okumak için önerilen yöntemi gösterir `numberOfChildren` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-142">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="be0a4-143">Null yapılabilir türleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="be0a4-143">Comparing Nullable Types</span></span>

<span data-ttu-id="be0a4-144">`Boolean`Boolean ifadelerde null yapılabilir değişkenler kullanıldığında, sonuç, `True` veya olabilir `False` `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-144">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="be0a4-145">Ve için Truth tablosu aşağıda verilmiştir `And` `Or` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-145">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="be0a4-146">`b1`Ve `b2` Şu anda üç olası değer olduğundan, değerlendirmek için dokuz birleşim vardır.</span><span class="sxs-lookup"><span data-stu-id="be0a4-146">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="be0a4-147">B1</span><span class="sxs-lookup"><span data-stu-id="be0a4-147">b1</span></span>|<span data-ttu-id="be0a4-148">B2</span><span class="sxs-lookup"><span data-stu-id="be0a4-148">b2</span></span>|<span data-ttu-id="be0a4-149">B1 ve B2</span><span class="sxs-lookup"><span data-stu-id="be0a4-149">b1 And b2</span></span>|<span data-ttu-id="be0a4-150">B1 veya B2</span><span class="sxs-lookup"><span data-stu-id="be0a4-150">b1 Or b2</span></span>|
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

<span data-ttu-id="be0a4-151">Bir Boole değişkeninin veya ifadesinin değeri olduğunda `Nothing` , ne `true` de değildir `false` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-151">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="be0a4-152">Aşağıdaki örneği inceleyin.</span><span class="sxs-lookup"><span data-stu-id="be0a4-152">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="be0a4-153">Bu örnekte, `b1 And b2` olarak değerlendirilir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-153">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="be0a4-154">Sonuç olarak, `Else` yan tümce her `If` ifadede yürütülür ve çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="be0a4-154">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="be0a4-155">`AndAlso` ve `OrElse` kısa devre değerlendirmesi kullanan, ilk olarak değerlendirilen ikinci işlenenlerini değerlendirmelidir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-155">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="be0a4-156">Yayma</span><span class="sxs-lookup"><span data-stu-id="be0a4-156">Propagation</span></span>

<span data-ttu-id="be0a4-157">Aritmetik, karşılaştırma, kaydırma veya tür işleminin işlenenlerinin bir veya her ikisi null yapılabilir bir değer türü ise, işlemin sonucu aynı zamanda null yapılabilir bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="be0a4-157">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="be0a4-158">Her iki işlenen de olmayan değerler içeriyorsa `Nothing` , işlem null yapılabilir bir değer türünde olmadığı gibi, işlenen değerlerinin temel alınarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-158">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="be0a4-159">Aşağıdaki örnekte, değişkenleri `compare1` ve `sum1` örtülü olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-159">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="be0a4-160">Fare işaretçisini bunlar üzerinde bekletirseniz, derleyicinin her ikisi için null yapılabilir değer türlerini ele alabileceğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="be0a4-160">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="be0a4-161">Bir veya iki işlenenin bir değeri varsa `Nothing` , sonuç olur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="be0a4-161">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="be0a4-162">Null yapılabilir türleri verilerle kullanma</span><span class="sxs-lookup"><span data-stu-id="be0a4-162">Using Nullable Types with Data</span></span>

<span data-ttu-id="be0a4-163">Veritabanı, null olabilen değer türlerini kullanmak için en önemli yerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="be0a4-163">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="be0a4-164">Tüm veritabanı nesneleri şu anda null yapılabilir değer türlerini desteklememektedir, ancak tasarımcı tarafından oluşturulan tablo bağdaştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="be0a4-164">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="be0a4-165">[Nullable türler Için TableAdapter desteği](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="be0a4-165">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="be0a4-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be0a4-166">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="be0a4-167">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="be0a4-167">Data Types</span></span>](index.md)
- [<span data-ttu-id="be0a4-168">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="be0a4-168">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="be0a4-169">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="be0a4-169">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="be0a4-170">TableAdapter'ları kullanarak veri kümelerini doldurma</span><span class="sxs-lookup"><span data-stu-id="be0a4-170">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="be0a4-171">If İşleci</span><span class="sxs-lookup"><span data-stu-id="be0a4-171">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="be0a4-172">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be0a4-172">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="be0a4-173">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="be0a4-173">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="be0a4-174">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="be0a4-174">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="be0a4-175">Nullable değer türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="be0a4-175">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
