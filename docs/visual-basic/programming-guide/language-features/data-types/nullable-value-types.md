---
title: "Boş Değer Atanabilen Değer Türleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="c2538-102">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2538-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="c2538-103">Bazen tanımlı bir değer bazı durumlarda sahip olmayan bir değer türü ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="c2538-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="c2538-104">Örneğin, bir veritabanı alanına anlamlı atanmış bir değere sahip ve atanmış bir değere sahip değil ayırt etmek zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2538-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="c2538-105">Değer türleri normal değerlerine veya null değeri olması için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2538-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="c2538-106">Böyle bir uzantı olarak adlandırılan bir *boş değer atanabilir tür*.</span><span class="sxs-lookup"><span data-stu-id="c2538-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="c2538-107">Boş değer atanabilir her tür genel oluşturulan <xref:System.Nullable%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="c2538-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="c2538-108">İş ilgili etkinlikleri izleyen bir veritabanı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c2538-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="c2538-109">Aşağıdaki örnek null atanabilir yapıları `Boolean` yazın ve bu tür bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="c2538-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="c2538-110">Üç yolla bildirimi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c2538-110">You can write the declaration in three ways:</span></span>  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 <span data-ttu-id="c2538-111">Değişkeni `ridesBusToWork` değerini tutabilir `True`, değerini `False`, ya da hiç herhangi bir değer.</span><span class="sxs-lookup"><span data-stu-id="c2538-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="c2538-112">İlk varsayılan değeri, bu durumda bilgileri henüz bu kişinin elde edilmiş değil olduğundan anlamına gelebilir hiçbir değer hiç olduğu.</span><span class="sxs-lookup"><span data-stu-id="c2538-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="c2538-113">Buna karşılık, `False` bilgi alınabilir ve kişi çalışmak için veri yolu ride değil anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c2538-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="c2538-114">Boş değer atanabilir türleri ile değişkenleri ve özellikleri bildirme ve bir dizi null atanabilir bir tür öğelerin bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2538-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="c2538-115">Parametre olarak boş değer atanabilir türler ile yordamları bildirebilir ve boş değer atanabilir bir tür döndürebilirsiniz bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2538-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="c2538-116">Boş değer atanabilir bir tür başvuru türünde bir dizi gibi oluşturamaz bir `String`, ya da bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="c2538-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="c2538-117">Temel alınan tür değeri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2538-117">The underlying type must be a value type.</span></span> <span data-ttu-id="c2538-118">Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c2538-118">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="c2538-119">Boş değer atanabilir tür değişken kullanma</span><span class="sxs-lookup"><span data-stu-id="c2538-119">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="c2538-120">Boş değer atanabilir bir tür en önemli üyeleri olan kendi <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="c2538-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="c2538-121">Boş değer atanabilir türde bir değişken için <xref:System.Nullable%601.HasValue%2A> değişkeni tanımlı bir değer içerip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2538-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="c2538-122">Varsa <xref:System.Nullable%601.HasValue%2A> olan `True`, değerini okuyabilirsiniz <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2538-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="c2538-123">Unutmayın her ikisi de <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> olan `ReadOnly` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="c2538-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="c2538-124">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="c2538-124">Default Values</span></span>  
 <span data-ttu-id="c2538-125">Bir değişken null atanabilir bir tür ile bildirirken kendi <xref:System.Nullable%601.HasValue%2A> özelliğinin varsayılan değeri `False`.</span><span class="sxs-lookup"><span data-stu-id="c2538-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="c2538-126">Başka bir deyişle, varsayılan olarak tanımlanan değeri, temel alınan değer türü varsayılan değeri yerine değişkeni yok.</span><span class="sxs-lookup"><span data-stu-id="c2538-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="c2538-127">Aşağıdaki örnekte, değişken `numberOfChildren` başlangıçta tanımlanan değeri, varsayılan değerini rağmen yok `Integer` türü: 0.</span><span class="sxs-lookup"><span data-stu-id="c2538-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 <span data-ttu-id="c2538-128">Null değeri tanımlanmamış veya bilinmeyen bir değer belirtmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2538-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="c2538-129">Varsa `numberOfChildren` olarak bildirilmiş `Integer`, bilgileri şu anda kullanılamıyor gösterebilir herhangi bir değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c2538-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="c2538-130">Değerlerini depolama</span><span class="sxs-lookup"><span data-stu-id="c2538-130">Storing Values</span></span>  
 <span data-ttu-id="c2538-131">Bir değeri bir değişken veya boş değer atanabilir bir tür özelliğine normal şekilde depolayın.</span><span class="sxs-lookup"><span data-stu-id="c2538-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="c2538-132">Aşağıdaki örnek değişkene değer atayan `numberOfChildren` önceki örnekte bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="c2538-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 <span data-ttu-id="c2538-133">Bir değişken veya boş değer atanabilir bir tür özelliği tanımlı bir değer içeriyorsa, atanmış bir değere sahip değil, ilk durumuna geri dönmek neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2538-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="c2538-134">Değişken ya da özelliğini ayarlayarak bunu `Nothing`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c2538-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="c2538-135">Atayabilirsiniz rağmen `Nothing` bir boş değer atanabilir türde bir değişkene için test edemiyor `Nothing` eşittir işaretinden kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c2538-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="c2538-136">Eşittir işareti kullanan karşılaştırma `someVar = Nothing`, her zaman değerlendiren `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2538-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="c2538-137">Değişkenin sınayabilirsiniz <xref:System.Nullable%601.HasValue%2A> özelliği için `False`, veya test kullanarak `Is` veya `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="c2538-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="c2538-138">Değerleri alma</span><span class="sxs-lookup"><span data-stu-id="c2538-138">Retrieving Values</span></span>  
 <span data-ttu-id="c2538-139">Boş değer atanabilir türde bir değişken değerini almak için önce sınamalısınız kendi <xref:System.Nullable%601.HasValue%2A> bir değer aldığından emin olmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="c2538-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="c2538-140">Değerini okumaya çalışırsanız, <xref:System.Nullable%601.HasValue%2A> olan `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] oluşturur bir <xref:System.InvalidOperationException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="c2538-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="c2538-141">Değişkeni okumak için önerilen yöntem aşağıdaki örnekte `numberOfChildren` önceki örneklerin.</span><span class="sxs-lookup"><span data-stu-id="c2538-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="c2538-142">Boş değer atanabilir türler karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="c2538-142">Comparing Nullable Types</span></span>  
 <span data-ttu-id="c2538-143">Boş değer atanabilir zaman `Boolean` değişkenleri Boolean ifadelerinde kullanılıyorsa, sonucu olabilir `True`, `False`, veya `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2538-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="c2538-144">Gerçekte tablodur aşağıdaki `And` ve `Or`.</span><span class="sxs-lookup"><span data-stu-id="c2538-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="c2538-145">Çünkü `b1` ve `b2` artık üç olası değerlere sahip değerlendirmek için dokuz birleşim vardır.</span><span class="sxs-lookup"><span data-stu-id="c2538-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="c2538-146">B1</span><span class="sxs-lookup"><span data-stu-id="c2538-146">b1</span></span>|<span data-ttu-id="c2538-147">B2</span><span class="sxs-lookup"><span data-stu-id="c2538-147">b2</span></span>|<span data-ttu-id="c2538-148">B1 ve b2</span><span class="sxs-lookup"><span data-stu-id="c2538-148">b1 And b2</span></span>|<span data-ttu-id="c2538-149">B1 veya b2</span><span class="sxs-lookup"><span data-stu-id="c2538-149">b1 Or b2</span></span>|  
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
  
 <span data-ttu-id="c2538-150">Ne zaman bir Boolean değişkeni veya ifade değeri `Nothing`, ne olduğunu `true` ya da `false`.</span><span class="sxs-lookup"><span data-stu-id="c2538-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="c2538-151">Aşağıdaki örnek göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c2538-151">Consider the following example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 <span data-ttu-id="c2538-152">Bu örnekte, `b1 And b2` değerlendiren `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2538-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="c2538-153">Sonuç olarak, `Else` yan tümcesi her yürütüldüğünde `If` deyimi ve çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c2538-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  <span data-ttu-id="c2538-154">`AndAlso`ve `OrElse`, kullanım, değerlendirme, kısa devre oluşturur gerekir değerlendirmek kendi ikinci işlenen ilk olarak değerlendirildiğinde `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2538-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="c2538-155">Yayma</span><span class="sxs-lookup"><span data-stu-id="c2538-155">Propagation</span></span>  
 <span data-ttu-id="c2538-156">Birini veya her ikisini bir aritmetik, karşılaştırma, SHIFT veya türü işlem işlenenleri boş değer atanabilir işleminin sonucu da null ise.</span><span class="sxs-lookup"><span data-stu-id="c2538-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="c2538-157">Her iki işlenen olmayan değerler içeriyorsa `Nothing`, ne değilmiş gibi işlem işlenenler temel değerlerine gerçekleştirilir null atanabilir bir tür.</span><span class="sxs-lookup"><span data-stu-id="c2538-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="c2538-158">Aşağıdaki örnekte, değişkenleri `compare1` ve `sum1` örtülü olarak yazılan.</span><span class="sxs-lookup"><span data-stu-id="c2538-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="c2538-159">Fare işaretçisini üzerine getirdiğinizde, derleyici boş değer atanabilir türler ikisinin için oluşturur olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c2538-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 <span data-ttu-id="c2538-160">Bir veya iki işlenen değeri varsa `Nothing`, sonucu olacaktır `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2538-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="c2538-161">Verilerle boş değer atanabilir türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c2538-161">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="c2538-162">Bir veritabanı, boş değer atanabilir türler kullanmak için en önemli basamak biridir.</span><span class="sxs-lookup"><span data-stu-id="c2538-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="c2538-163">Tüm veritabanı nesneleri şu anda boş değer atanabilir türler destekler, ancak Tablo Tasarımcısı tarafından oluşturulan bağdaştırıcıları yapın.</span><span class="sxs-lookup"><span data-stu-id="c2538-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="c2538-164">"Boş değer atanabilir türler için TableAdapter destek" bölümüne bakın [TableAdapter genel bakışı](/visualstudio/data-tools/tableadapter-overview).</span><span class="sxs-lookup"><span data-stu-id="c2538-164">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2538-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2538-165">See Also</span></span>  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [<span data-ttu-id="c2538-166">Boş değer atanabilir türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c2538-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="c2538-167">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="c2538-167">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="c2538-168">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="c2538-168">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="c2538-169">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c2538-169">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="c2538-170">TableAdapter genel bakış</span><span class="sxs-lookup"><span data-stu-id="c2538-170">TableAdapter Overview</span></span>](/visualstudio/data-tools/tableadapter-overview)  
 [<span data-ttu-id="c2538-171">Varsa işleci</span><span class="sxs-lookup"><span data-stu-id="c2538-171">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="c2538-172">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="c2538-172">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="c2538-173">Is işleci</span><span class="sxs-lookup"><span data-stu-id="c2538-173">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="c2538-174">IsNot işleci</span><span class="sxs-lookup"><span data-stu-id="c2538-174">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
