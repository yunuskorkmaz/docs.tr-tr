---
title: Boş değer atanabilen değer türleri - Visual Basic
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
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921318"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="fccba-102">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fccba-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="fccba-103">Bazen belirli durumlarda tanımlı bir değer olmayan bir değer türü ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="fccba-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="fccba-104">Örneğin, bir veritabanı bir alana atanan bir değere sahip değil ve anlamlı atanan bir değere sahip arasında ayırt etmek olabilir.</span><span class="sxs-lookup"><span data-stu-id="fccba-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="fccba-105">Değer türleri, normal değerlerini veya null değeri olması için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="fccba-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="fccba-106">Böyle bir uzantı olarak adlandırılan bir *boş değer atanabilir tür*.</span><span class="sxs-lookup"><span data-stu-id="fccba-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="fccba-107">Her bir boş değer atanabilir tür genel oluşturulan <xref:System.Nullable%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="fccba-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="fccba-108">İşle ilgili etkinlikler izleyen bir veritabanı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fccba-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="fccba-109">Aşağıdaki örnek bir boş değer atanabilir yapıları `Boolean` yazın ve bu tür bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="fccba-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="fccba-110">Bildirim üç şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fccba-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="fccba-111">Değişken `ridesBusToWork` değerini tutabilen `True`, değerini `False`, ya da hiç değer.</span><span class="sxs-lookup"><span data-stu-id="fccba-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="fccba-112">İlk varsayılan değeri yok, hangi bilgilerin henüz bu kişinin elde edilmiş değil, bu durumda gelebilir değerdir.</span><span class="sxs-lookup"><span data-stu-id="fccba-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="fccba-113">Buna karşılık, `False` bilgi edinmiş olması ve kişi çalışmak için veri yolu bulutumuzda değil anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="fccba-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="fccba-114">Boş değer atanabilir türler ile değişkenleri ve özellikleri bildirme ve bir dizi öğelerini boş değer atanabilir bir tür bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fccba-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="fccba-115">Parametre olarak boş değer atanabilir tiplerde yordamları bildirebilir ve boş değer atanabilir bir tür döndürebilir bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="fccba-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="fccba-116">Bir dizi gibi bir başvuru türü üzerinde boş değer atanabilir bir tür oluşturulamaz bir `String`, veya bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="fccba-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="fccba-117">Temel alınan türü bir değer türü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fccba-117">The underlying type must be a value type.</span></span> <span data-ttu-id="fccba-118">Daha fazla bilgi için [değer türleri ve başvuru türleri](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="fccba-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="fccba-119">Boş değer atanabilir tür değişken kullanma</span><span class="sxs-lookup"><span data-stu-id="fccba-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="fccba-120">Boş değer atanabilir bir tür en önemli üyeleri kendi <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fccba-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="fccba-121">Boş değer atanabilir bir türde bir değişken için <xref:System.Nullable%601.HasValue%2A> değişkeni tanımlı bir değer içerip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fccba-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="fccba-122">Varsa <xref:System.Nullable%601.HasValue%2A> olduğu `True`, değerini okuyabilirsiniz <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="fccba-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="fccba-123">Unutmayın hem <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> olan `ReadOnly` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fccba-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="fccba-124">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="fccba-124">Default Values</span></span>

<span data-ttu-id="fccba-125">Null yapılabilir bir tür bir değişken bildirdiğinizde, <xref:System.Nullable%601.HasValue%2A> özelliği varsayılan değerine sahip `False`.</span><span class="sxs-lookup"><span data-stu-id="fccba-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="fccba-126">Bu, varsayılan olarak, kendi temel değer türünün varsayılan değeri yerine tanımlı hiçbir değer değişkeni olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fccba-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="fccba-127">Aşağıdaki örnekte, değişken `numberOfChildren` tanımlanmış hiçbir değer olsa bile varsayılan değerine sahip başlangıçta `Integer` türü: 0.</span><span class="sxs-lookup"><span data-stu-id="fccba-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="fccba-128">Bir null değer tanımsız veya bilinmeyen bir değeri belirtmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="fccba-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="fccba-129">Varsa `numberOfChildren` olarak bildirilmiş `Integer`, bilgileri şu anda kullanılabilir değil oluşturabilecek herhangi bir değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fccba-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="fccba-130">Değerlerini depolama</span><span class="sxs-lookup"><span data-stu-id="fccba-130">Storing Values</span></span>

<span data-ttu-id="fccba-131">Bir değer bir değişken veya özellik boş değer atanabilir bir tür içinde normal şekilde depolayın.</span><span class="sxs-lookup"><span data-stu-id="fccba-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="fccba-132">Aşağıdaki örnek bir değişkene bir değer atar `numberOfChildren` önceki örnekte bildirilen.</span><span class="sxs-lookup"><span data-stu-id="fccba-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="fccba-133">Bir değişken veya boş değer atanabilir bir tür özelliği tanımlı bir değer içeriyorsa, atanan bir değere sahip değil, ilk durumuna geri dönmek neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fccba-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="fccba-134">Değişken veya özelliğini ayarlayarak bunu `Nothing`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fccba-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="fccba-135">Atayabilseniz `Nothing` boş değer atanabilir bir tür bir değişken için sizin için test edilemez `Nothing` eşittir işareti kullanılarak.</span><span class="sxs-lookup"><span data-stu-id="fccba-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="fccba-136">Eşittir işareti kullanan karşılaştırma `someVar = Nothing`, her zaman değerlendirilir `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fccba-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="fccba-137">Değişkenin sınayabilirsiniz <xref:System.Nullable%601.HasValue%2A> özelliği `False`, veya test kullanarak `Is` veya `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="fccba-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="fccba-138">Değerlerini alma</span><span class="sxs-lookup"><span data-stu-id="fccba-138">Retrieving Values</span></span>

<span data-ttu-id="fccba-139">Boş değer atanabilir bir tür değişkeninin değerini almak için önce test etmelisiniz kendi <xref:System.Nullable%601.HasValue%2A> özellik değeri olduğundan emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="fccba-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="fccba-140">Değeri okunamıyor çalışırsanız, <xref:System.Nullable%601.HasValue%2A> olduğu `False`, Visual Basic oluşturur bir <xref:System.InvalidOperationException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="fccba-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="fccba-141">Aşağıdaki örnek, değişken okumak için önerilen yol gösterir. `numberOfChildren` önceki örneklerin.</span><span class="sxs-lookup"><span data-stu-id="fccba-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="fccba-142">Boş değer atanabilir türler karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fccba-142">Comparing Nullable Types</span></span>

<span data-ttu-id="fccba-143">Boş değer atanabilir olduğunda `Boolean` değişkenleri, Boolean ifadeleri kullanılır, sonucu olabilir `True`, `False`, veya `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fccba-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="fccba-144">Gerçekte tablosudur aşağıdaki `And` ve `Or`.</span><span class="sxs-lookup"><span data-stu-id="fccba-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="fccba-145">Çünkü `b1` ve `b2` artık üç olası değer vardır değerlendirilecek dokuz birleşimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="fccba-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="fccba-146">b1</span><span class="sxs-lookup"><span data-stu-id="fccba-146">b1</span></span>|<span data-ttu-id="fccba-147">b2</span><span class="sxs-lookup"><span data-stu-id="fccba-147">b2</span></span>|<span data-ttu-id="fccba-148">B1 ve b2</span><span class="sxs-lookup"><span data-stu-id="fccba-148">b1 And b2</span></span>|<span data-ttu-id="fccba-149">B1 veya b2</span><span class="sxs-lookup"><span data-stu-id="fccba-149">b1 Or b2</span></span>|
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

<span data-ttu-id="fccba-150">Bir Boolean değişkenin veya ifadenin değerini olduğunda `Nothing`, ne olduğunu `true` ya da `false`.</span><span class="sxs-lookup"><span data-stu-id="fccba-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="fccba-151">Aşağıdaki örnek göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fccba-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="fccba-152">Bu örnekte, `b1 And b2` değerlendiren `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fccba-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="fccba-153">Sonuç olarak, `Else` yan tümcesi her yürütüldüğünde `If` bildirimi ve çıktı şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fccba-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` <span data-ttu-id="fccba-154">ve `OrElse`, kullanım, değerlendirme, kısa devre oluşturur gerekir değerlendirmek için ikinci işlenenleri ilk olarak değerlendirildiğinde `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fccba-154">and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="fccba-155">Yayma</span><span class="sxs-lookup"><span data-stu-id="fccba-155">Propagation</span></span>

<span data-ttu-id="fccba-156">Birini veya her ikisini işlenenlerin aritmetik, karşılaştırma, kaydırma veya türü işlem, boş değer atanabilir işleminin sonucu ayrıca boş değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="fccba-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="fccba-157">Her iki işlenen de olmayan değerlere sahip `Nothing`, ne gibi temel alınan değerlerin işlenenden işlemin gerçekleştirilmesinden boş değer atanabilir bir tür.</span><span class="sxs-lookup"><span data-stu-id="fccba-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="fccba-158">Aşağıdaki örnekte, değişken `compare1` ve `sum1` örtük olarak belirlenmiş.</span><span class="sxs-lookup"><span data-stu-id="fccba-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="fccba-159">Bunlar üzerinde fare işaretçisini getirdiğinizde, derleyici boş değer atanabilir türler ikisinin için çıkarsar olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fccba-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="fccba-160">Bir veya iki işlenenin değerini varsa `Nothing`, sonuç olacaktır `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fccba-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="fccba-161">Verilerle boş değer atanabilir türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="fccba-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="fccba-162">Boş değer atanabilir türler kullanmak için en önemli yerlerden biri bir veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="fccba-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="fccba-163">Tüm veritabanı nesneleri şu anda boş değer atanabilir türler desteklese de, tasarımcı tarafından oluşturulan tablo bağdaştırıcıları yapın.</span><span class="sxs-lookup"><span data-stu-id="fccba-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="fccba-164">Bkz: [boş değer atanabilir türler için TableAdapter desteği](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="fccba-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="fccba-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fccba-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="fccba-166">Boş Değer Atanabilir Türleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="fccba-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="fccba-167">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fccba-167">Data Types</span></span>](index.md)
- [<span data-ttu-id="fccba-168">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="fccba-168">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="fccba-169">Veri Türleri Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fccba-169">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="fccba-170">TableAdapters'ı kullanarak veri kümelerini doldurma</span><span class="sxs-lookup"><span data-stu-id="fccba-170">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="fccba-171">If İşleci</span><span class="sxs-lookup"><span data-stu-id="fccba-171">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="fccba-172">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fccba-172">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="fccba-173">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="fccba-173">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="fccba-174">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="fccba-174">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)