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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249688"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="babf0-102">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="babf0-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="babf0-103">Bazen belirli durumlarda tanımlı bir değeri olmayan bir değer türüyle çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="babf0-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="babf0-104">Örneğin, veritabanındaki bir alanın anlamlı olan atanmış bir değere sahip olmakla atanmış bir değere sahip olmamak arasında ayrım yapmak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="babf0-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="babf0-105">Değer türleri normal değerlerini veya null değerini alacak şekilde genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="babf0-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="babf0-106">Böyle bir uzantı *geçersiz*türü olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="babf0-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="babf0-107">Her nullable değer türü genel <xref:System.Nullable%601> yapıdan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="babf0-107">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="babf0-108">İşle ilgili etkinlikleri izleyen bir veritabanı düşünün.</span><span class="sxs-lookup"><span data-stu-id="babf0-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="babf0-109">Aşağıdaki örnek, nullable `Boolean` türü inşa eder ve bu tür bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="babf0-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="babf0-110">Bildirimi üç şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="babf0-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="babf0-111">Değişken, `ridesBusToWork` bir değer , bir `False`değer veya hiç değer tutabilir. `True`</span><span class="sxs-lookup"><span data-stu-id="babf0-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="babf0-112">İlk varsayılan değeri hiç bir değer değildir, bu durumda bu kişi için bilgi henüz elde edilmemiştir anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="babf0-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="babf0-113">Buna karşılık, `False` bilgi elde edilmiş ve kişi işe otobüse binmek değil anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="babf0-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="babf0-114">Değişkenleri ve özellikleri nullable değer türleri ile bildirebilir ve nullable değer türü öğeleri ile bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="babf0-114">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="babf0-115">Nullable değer türleri olan yordamları parametre olarak bildirebilir ve bir `Function` yordamdan nullable değer türü döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="babf0-115">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="babf0-116">Bir dizi, bir `String`, veya bir sınıf gibi bir başvuru türü üzerinde geçersiz bir tür oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="babf0-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="babf0-117">Temel türü bir değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="babf0-117">The underlying type must be a value type.</span></span> <span data-ttu-id="babf0-118">Daha fazla bilgi için [Bkz. Değer Türleri ve Başvuru Türleri.](value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="babf0-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="babf0-119">Nullable Tip Değişkeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="babf0-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="babf0-120">Nullable değer türünün en önemli <xref:System.Nullable%601.HasValue%2A> üyeleri <xref:System.Nullable%601.Value%2A> onun ve özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="babf0-120">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="babf0-121">Nullable değer türünden bir <xref:System.Nullable%601.HasValue%2A> değişken için, değişkentanımlı bir değer iyp etmediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="babf0-121">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="babf0-122">Ise, <xref:System.Nullable%601.HasValue%2A> değerini <xref:System.Nullable%601.Value%2A> `True`</span><span class="sxs-lookup"><span data-stu-id="babf0-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="babf0-123">Her ikisinin <xref:System.Nullable%601.Value%2A> `ReadOnly` de <xref:System.Nullable%601.HasValue%2A> ve özelliklerinin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="babf0-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="babf0-124">Varsayılan Değerler</span><span class="sxs-lookup"><span data-stu-id="babf0-124">Default Values</span></span>

<span data-ttu-id="babf0-125">Nullable değer türüne sahip bir değişken <xref:System.Nullable%601.HasValue%2A> idacattığınızda, özelliği `False`varsayılan değeri .</span><span class="sxs-lookup"><span data-stu-id="babf0-125">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="babf0-126">Bu, varsayılan olarak değişkenin temel değer türünün varsayılan değeri yerine tanımlı bir değeri olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="babf0-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="babf0-127">Aşağıdaki örnekte, `numberOfChildren` `Integer` türün varsayılan değeri 0 olsa bile, değişkenin başlangıçta tanımlı bir değeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="babf0-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="babf0-128">Null değeri tanımlanmamış veya bilinmeyen bir değeri belirtmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="babf0-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="babf0-129">Olarak `numberOfChildren` bildirilmiş `Integer`olsaydı, bilgilerin şu anda kullanılmadığını gösteren hiçbir değer olmazdı.</span><span class="sxs-lookup"><span data-stu-id="babf0-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="babf0-130">Değerleri Depolama</span><span class="sxs-lookup"><span data-stu-id="babf0-130">Storing Values</span></span>

<span data-ttu-id="babf0-131">Bir değeri, normal bir şekilde geçersiz bir değer türünde veya değişken desiyerinde saklarsınız.</span><span class="sxs-lookup"><span data-stu-id="babf0-131">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="babf0-132">Aşağıdaki örnek, önceki örnekte `numberOfChildren` bildirilen değişkene bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="babf0-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="babf0-133">Geçersiz bir değer türünün değişkeni veya özelliği tanımlı bir değer içeriyorsa, bir değer atanmış olmayan ilk durumuna geri dönülmesine neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="babf0-133">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="babf0-134">Bunu, aşağıdaki örnekte görüldüğü `Nothing`gibi değişkeni veya özelliği , olarak ayarlayarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="babf0-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="babf0-135">Nullable değer `Nothing` türünden bir değişkene atayabilirsiniz, ancak `Nothing` eşit işareti kullanarak bunu sınayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="babf0-135">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="babf0-136">Eşit işareti kullanan karşılaştırma, `someVar = Nothing`her zaman `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="babf0-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="babf0-137">Değişkenin <xref:System.Nullable%601.HasValue%2A> özelliğini `False`veya testini veya işleci `IsNot` kullanarak test edebilirsiniz. `Is`</span><span class="sxs-lookup"><span data-stu-id="babf0-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="babf0-138">Değerleri Alma</span><span class="sxs-lookup"><span data-stu-id="babf0-138">Retrieving Values</span></span>

<span data-ttu-id="babf0-139">Nullable değer türünden bir değişkenin değerini almak için, <xref:System.Nullable%601.HasValue%2A> önce bir değeri olduğunu doğrulamak için özelliğini sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="babf0-139">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="babf0-140">Değeri ne zaman <xref:System.Nullable%601.HasValue%2A> okumaya `False`çalışırsanız, Visual Basic <xref:System.InvalidOperationException> bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="babf0-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="babf0-141">Aşağıdaki örnek, önceki örneklerin değişkenini `numberOfChildren` okumanın önerilen yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="babf0-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="babf0-142">Nullable Türleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="babf0-142">Comparing Nullable Types</span></span>

<span data-ttu-id="babf0-143">Boolean `Boolean` ifadelerinde nullable değişkenler kullanıldığında, sonuç `True`, `False`, `Nothing`veya .</span><span class="sxs-lookup"><span data-stu-id="babf0-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="babf0-144">Aşağıdaki için gerçek tablo `And` `Or`ve .</span><span class="sxs-lookup"><span data-stu-id="babf0-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="babf0-145">Çünkü `b1` `b2` ve şimdi üç olası değerleri var, değerlendirmek için dokuz kombinasyonları vardır.</span><span class="sxs-lookup"><span data-stu-id="babf0-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="babf0-146">b1</span><span class="sxs-lookup"><span data-stu-id="babf0-146">b1</span></span>|<span data-ttu-id="babf0-147">B2</span><span class="sxs-lookup"><span data-stu-id="babf0-147">b2</span></span>|<span data-ttu-id="babf0-148">b1 Ve b2</span><span class="sxs-lookup"><span data-stu-id="babf0-148">b1 And b2</span></span>|<span data-ttu-id="babf0-149">b1 Veya b2</span><span class="sxs-lookup"><span data-stu-id="babf0-149">b1 Or b2</span></span>|
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

<span data-ttu-id="babf0-150">Bir Boolean değişkeninin veya `Nothing`ifadesinin değeri `true` `false`ne de .</span><span class="sxs-lookup"><span data-stu-id="babf0-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="babf0-151">Aşağıdaki örneği inceleyin.</span><span class="sxs-lookup"><span data-stu-id="babf0-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="babf0-152">Bu örnekte, `b1 And b2` '' `Nothing`</span><span class="sxs-lookup"><span data-stu-id="babf0-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="babf0-153">Sonuç olarak, `Else` yan tümce `If` her deyimde yürütülür ve çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="babf0-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="babf0-154">`AndAlso`ve `OrElse`kısa devre değerlendirmesini kullanan, ikinci operandları değerlendirmek `Nothing`zorundadır.</span><span class="sxs-lookup"><span data-stu-id="babf0-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="babf0-155">Yayma</span><span class="sxs-lookup"><span data-stu-id="babf0-155">Propagation</span></span>

<span data-ttu-id="babf0-156">Bir aritmetik, karşılaştırma, kaydırma veya tür işleminin operandlarından biri veya her ikisi geçersiz bir değer türüyse, işlemin sonucu da geçersiz bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="babf0-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="babf0-157">Her iki operands olmayan `Nothing`değerlervarsa, işlem operands temel değerleri üzerinde gerçekleştirilir, sanki ne nullable değer türü idi.</span><span class="sxs-lookup"><span data-stu-id="babf0-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="babf0-158">Aşağıdaki örnekte, `compare1` değişkenler `sum1` ve örtülü olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="babf0-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="babf0-159">Fare işaretçisini üzerlerine dinlendirmek durumunda, derleyicinin her ikisi için de geçersiz değer türlerini çıkardığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="babf0-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="babf0-160">Bir veya her iki operands `Nothing`bir değeri `Nothing`varsa , sonuç olacaktır.</span><span class="sxs-lookup"><span data-stu-id="babf0-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="babf0-161">Verilerle Nullable Türleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="babf0-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="babf0-162">Veritabanı, nullable değer türlerini kullanmak için en önemli yerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="babf0-162">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="babf0-163">Tüm veritabanı nesneleri şu anda geçersiz değer türlerini desteklemez, ancak tasarımcı tarafından oluşturulan tablo bağdaştırıcıları destekler.</span><span class="sxs-lookup"><span data-stu-id="babf0-163">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="babf0-164">[Nullable türleri için TableAdapter desteğine](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)bakın.</span><span class="sxs-lookup"><span data-stu-id="babf0-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="babf0-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="babf0-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="babf0-166">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="babf0-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="babf0-167">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="babf0-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="babf0-168">Veri Türleri Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="babf0-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="babf0-169">TableAdapter'ları kullanarak veri kümelerini doldurma</span><span class="sxs-lookup"><span data-stu-id="babf0-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="babf0-170">If İşleci</span><span class="sxs-lookup"><span data-stu-id="babf0-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="babf0-171">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="babf0-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="babf0-172">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="babf0-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="babf0-173">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="babf0-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="babf0-174">Nullable Değer Türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="babf0-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
