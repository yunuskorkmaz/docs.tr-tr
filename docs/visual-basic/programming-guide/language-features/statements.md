---
title: Deyimler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: 09fe53f4bc2b6d025b762c6595c5337263456bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401985"
---
# <a name="statements-in-visual-basic"></a><span data-ttu-id="695f7-102">Visual Basic'deki Deyimler</span><span class="sxs-lookup"><span data-stu-id="695f7-102">Statements in Visual Basic</span></span>

<span data-ttu-id="695f7-103">Visual Basic bir ifade, bir bütün yönergedir.</span><span class="sxs-lookup"><span data-stu-id="695f7-103">A statement in Visual Basic is a complete instruction.</span></span> <span data-ttu-id="695f7-104">Anahtar sözcükler, işleçler, değişkenler, sabitler ve ifadeler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-104">It can contain keywords, operators, variables, constants, and expressions.</span></span> <span data-ttu-id="695f7-105">Her bir ekstre aşağıdaki kategorilerden birine aittir:</span><span class="sxs-lookup"><span data-stu-id="695f7-105">Each statement belongs to one of the following categories:</span></span>

- <span data-ttu-id="695f7-106">Bir değişken, sabit veya yordamı belirleyen ve ayrıca bir veri türü de içerebilen **bildirim deyimleri**.</span><span class="sxs-lookup"><span data-stu-id="695f7-106">**Declaration Statements**, which name a variable, constant, or procedure, and can also specify a data type.</span></span>

- <span data-ttu-id="695f7-107">Eylem başlatan **çalıştırılabilir deyimler**.</span><span class="sxs-lookup"><span data-stu-id="695f7-107">**Executable Statements**, which initiate actions.</span></span> <span data-ttu-id="695f7-108">Bu deyimler bir yöntemi veya işlevi çağırabilir ve kod blokları aracılığıyla döngü ya da dallarda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-108">These statements can call a method or function, and they can loop or branch through blocks of code.</span></span> <span data-ttu-id="695f7-109">Executable deyimleri, bir değişkene veya sabitine bir değer veya ifade atayan **atama deyimlerini**içerir.</span><span class="sxs-lookup"><span data-stu-id="695f7-109">Executable statements include **Assignment Statements**, which assign a value or expression to a variable or constant.</span></span>

<span data-ttu-id="695f7-110">Bu konuda her kategori açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="695f7-110">This topic describes each category.</span></span> <span data-ttu-id="695f7-111">Ayrıca, bu konu, birden çok deyimin tek bir satırda nasıl birleştirileceğini ve birden çok satır üzerinde bir ifadeye nasıl devam edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="695f7-111">Also, this topic describes how to combine multiple statements on a single line and how to continue a statement over multiple lines.</span></span>

## <a name="declaration-statements"></a><span data-ttu-id="695f7-112">Bildirim deyimleri</span><span class="sxs-lookup"><span data-stu-id="695f7-112">Declaration statements</span></span>

<span data-ttu-id="695f7-113">Yordamlar, değişkenler, özellikler, diziler ve sabitleri adlandırmak ve tanımlamak için bildirim deyimlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="695f7-113">You use declaration statements to name and define procedures, variables, properties, arrays, and constants.</span></span> <span data-ttu-id="695f7-114">Bir programlama öğesi bildirdiğinizde, veri türünü, erişim düzeyini ve kapsamını da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-114">When you declare a programming element, you can also define its data type, access level, and scope.</span></span> <span data-ttu-id="695f7-115">Daha fazla bilgi için bkz. [bildirilmemiş öğe özellikleri](./declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-115">For more information, see [Declared Element Characteristics](./declared-elements/declared-element-characteristics.md).</span></span>

<span data-ttu-id="695f7-116">Aşağıdaki örnek üç bildirim içerir.</span><span class="sxs-lookup"><span data-stu-id="695f7-116">The following example contains three declarations.</span></span>

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

<span data-ttu-id="695f7-117">İlk bildirim, `Sub` deyimidir.</span><span class="sxs-lookup"><span data-stu-id="695f7-117">The first declaration is the `Sub` statement.</span></span> <span data-ttu-id="695f7-118">Eşleşen `End Sub` ifadesiyle birlikte, adlı bir yordamı bildirir `applyFormat` .</span><span class="sxs-lookup"><span data-stu-id="695f7-118">Together with its matching `End Sub` statement, it declares a procedure named `applyFormat`.</span></span> <span data-ttu-id="695f7-119">Ayrıca bunu belirtir `applyFormat` ; yani `Public` , başvurabilen tüm kodlar bunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-119">It also specifies that `applyFormat` is `Public`, which means that any code that can refer to it can call it.</span></span>

<span data-ttu-id="695f7-120">İkinci bildirim, `Const` `limit` `Integer` veri türünü ve 33 değerini belirterek sabiti bildiren ifadedir.</span><span class="sxs-lookup"><span data-stu-id="695f7-120">The second declaration is the `Const` statement, which declares the constant `limit`, specifying the `Integer` data type and a value of 33.</span></span>

<span data-ttu-id="695f7-121">Üçüncü bildirim, `Dim` değişkeni bildiren deyimidir `thisWidget` .</span><span class="sxs-lookup"><span data-stu-id="695f7-121">The third declaration is the `Dim` statement, which declares the variable `thisWidget`.</span></span> <span data-ttu-id="695f7-122">Veri türü, sınıfından oluşturulan bir nesne olarak belirtilen belirli bir nesnedir `Widget` .</span><span class="sxs-lookup"><span data-stu-id="695f7-122">The data type is a specific object, namely an object created from the `Widget` class.</span></span> <span data-ttu-id="695f7-123">Bir değişkeni, herhangi bir temel veri türü veya kullandığınız uygulamada kullanıma sunulan herhangi bir nesne türünde olacak şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-123">You can declare a variable to be of any elementary data type or of any object type that is exposed in the application you are using.</span></span>

### <a name="initial-values"></a><span data-ttu-id="695f7-124">İlk değerler</span><span class="sxs-lookup"><span data-stu-id="695f7-124">Initial Values</span></span>

<span data-ttu-id="695f7-125">Bir bildirim ifadesini içeren kod çalıştırıldığında, Visual Basic bildirimi yapılan öğe için gereken belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="695f7-125">When the code containing a declaration statement runs, Visual Basic reserves the memory required for the declared element.</span></span> <span data-ttu-id="695f7-126">Öğe bir değer içeriyorsa, Visual Basic onu veri türü için varsayılan değer olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="695f7-126">If the element holds a value, Visual Basic initializes it to the default value for its data type.</span></span> <span data-ttu-id="695f7-127">Daha fazla bilgi için, bkz. [Dim deyimindeki](../../language-reference/statements/dim-statement.md)"davranış".</span><span class="sxs-lookup"><span data-stu-id="695f7-127">For more information, see "Behavior" in [Dim Statement](../../language-reference/statements/dim-statement.md).</span></span>

<span data-ttu-id="695f7-128">Aşağıdaki örnekte gösterildiği gibi, bir değişkene, bildiriminin bir parçası olarak bir başlangıç değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-128">You can assign an initial value to a variable as part of its declaration, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

<span data-ttu-id="695f7-129">Bir değişken bir nesne değişkense, aşağıdaki örnekte gösterildiği gibi [New Operator](../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak sınıfını bildirdiğinizde sınıfının bir örneğini açıkça oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-129">If a variable is an object variable, you can explicitly create an instance of its class when you declare it by using the [New Operator](../../language-reference/operators/new-operator.md) keyword, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

<span data-ttu-id="695f7-130">Bir bildirim ifadesinde belirttiğiniz ilk değerin, yürütme bildirim bildirimine ulaşıncaya kadar bir değişkene atanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="695f7-130">Note that the initial value you specify in a declaration statement is not assigned to a variable until execution reaches its declaration statement.</span></span> <span data-ttu-id="695f7-131">Bu saate kadar, değişken veri türü için varsayılan değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="695f7-131">Until that time, the variable contains the default value for its data type.</span></span>

## <a name="executable-statements"></a><span data-ttu-id="695f7-132">Yürütülebilir deyimler</span><span class="sxs-lookup"><span data-stu-id="695f7-132">Executable statements</span></span>

<span data-ttu-id="695f7-133">Yürütülebilir bir ifade bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="695f7-133">An executable statement performs an action.</span></span> <span data-ttu-id="695f7-134">Bir yordam çağırabilir, koddaki başka bir yere dallandırır, çeşitli deyimlerde döngü gerçekleştirebilir veya bir ifadeyi değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-134">It can call a procedure, branch to another place in the code, loop through several statements, or evaluate an expression.</span></span> <span data-ttu-id="695f7-135">Atama ekstresi, yürütülebilir bir deyimin özel bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="695f7-135">An assignment statement is a special case of an executable statement.</span></span>

<span data-ttu-id="695f7-136">Aşağıdaki örnek, `If...Then...Else` bir değişkenin değerine göre farklı kod blokları çalıştırmak için bir denetim yapısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="695f7-136">The following example uses an `If...Then...Else` control structure to run different blocks of code based on the value of a variable.</span></span> <span data-ttu-id="695f7-137">Her kod bloğu içinde, bir `For...Next` döngü belirtilen sayıda çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="695f7-137">Within each block of code, a `For...Next` loop runs a specified number of times.</span></span>

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

<span data-ttu-id="695f7-138">`If`Önceki örnekteki ifade, parametresinin değerini denetler `clockwise` .</span><span class="sxs-lookup"><span data-stu-id="695f7-138">The `If` statement in the preceding example checks the value of the parameter `clockwise`.</span></span> <span data-ttu-id="695f7-139">Değer ise, `True` `spinClockwise` yöntemini çağırır `aWidget` .</span><span class="sxs-lookup"><span data-stu-id="695f7-139">If the value is `True`, it calls the `spinClockwise` method of `aWidget`.</span></span> <span data-ttu-id="695f7-140">Değer ise, `False` `spinCounterClockwise` yöntemini çağırır `aWidget` .</span><span class="sxs-lookup"><span data-stu-id="695f7-140">If the value is `False`, it calls the `spinCounterClockwise` method of `aWidget`.</span></span> <span data-ttu-id="695f7-141">`If...Then...Else`Denetim yapısı ile biter `End If` .</span><span class="sxs-lookup"><span data-stu-id="695f7-141">The `If...Then...Else` control structure ends with `End If`.</span></span>

<span data-ttu-id="695f7-142">`For...Next`Her bloğun içindeki döngü, parametrenin değerine eşit sayıda kez uygun yöntemi çağırır `revolutions` .</span><span class="sxs-lookup"><span data-stu-id="695f7-142">The `For...Next` loop within each block calls the appropriate method a number of times equal to the value of the `revolutions` parameter.</span></span>

## <a name="assignment-statements"></a><span data-ttu-id="695f7-143">Atama deyimleri</span><span class="sxs-lookup"><span data-stu-id="695f7-143">Assignment statements</span></span>

<span data-ttu-id="695f7-144">Atama deyimleri, atama işlecinin () sağ tarafında değeri alan `=` ve bunu, aşağıdaki örnekte olduğu gibi soldaki öğede depolayan atama işlemlerini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-144">Assignment statements carry out assignment operations, which consist of taking the value on the right side of the assignment operator (`=`) and storing it in the element on the left, as in the following example.</span></span>

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

<span data-ttu-id="695f7-145">Yukarıdaki örnekte, atama bildiriminde 42 sabit değeri, değişkende saklanır `v` .</span><span class="sxs-lookup"><span data-stu-id="695f7-145">In the preceding example, the assignment statement stores the literal value 42 in the variable `v`.</span></span>

### <a name="eligible-programming-elements"></a><span data-ttu-id="695f7-146">Uygun programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="695f7-146">Eligible programming elements</span></span>

<span data-ttu-id="695f7-147">Atama işlecinin sol tarafındaki programlama öğesi bir değeri kabul edip depolayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="695f7-147">The programming element on the left side of the assignment operator must be able to accept and store a value.</span></span> <span data-ttu-id="695f7-148">Bu, [salt okunur](../../language-reference/modifiers/readonly.md)olmayan bir değişken veya özellik olması veya bir dizi öğesi olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="695f7-148">This means it must be a variable or property that is not [ReadOnly](../../language-reference/modifiers/readonly.md), or it must be an array element.</span></span> <span data-ttu-id="695f7-149">Atama ifadesinin bağlamında, bu tür bir öğe bazen "sol değer" için *lvalue*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="695f7-149">In the context of an assignment statement, such an element is sometimes called an *lvalue*, for "left value."</span></span>

<span data-ttu-id="695f7-150">Atama işlecinin sağ tarafındaki değer, değişmez değer, sabitler, değişkenler, özellikler, dizi öğeleri, diğer ifadeler veya işlev çağrılarının birleşiminden oluşabilen bir ifade tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="695f7-150">The value on the right side of the assignment operator is generated by an expression, which can consist of any combination of literals, constants, variables, properties, array elements, other expressions, or function calls.</span></span> <span data-ttu-id="695f7-151">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="695f7-151">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

<span data-ttu-id="695f7-152">Yukarıdaki örnek, değişkenine tutulan değeri `y` değişkeninde bulunan değere ekler `z` ve sonra çağrısı tarafından döndürülen değeri işlevine ekler `findResult` .</span><span class="sxs-lookup"><span data-stu-id="695f7-152">The preceding example adds the value held in variable `y` to the value held in variable `z`, and then adds the value returned by the call to function `findResult`.</span></span> <span data-ttu-id="695f7-153">Bu ifadenin toplam değeri daha sonra değişkende depolanır `x` .</span><span class="sxs-lookup"><span data-stu-id="695f7-153">The total value of this expression is then stored in variable `x`.</span></span>

### <a name="data-types-in-assignment-statements"></a><span data-ttu-id="695f7-154">Atama İfadelerdeki veri türleri</span><span class="sxs-lookup"><span data-stu-id="695f7-154">Data types in assignment statements</span></span>

<span data-ttu-id="695f7-155">Sayısal değerlere ek olarak, aşağıdaki örnekte gösterildiği gibi atama işleci de `String` değerler atayabilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-155">In addition to numeric values, the assignment operator can also assign `String` values, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

<span data-ttu-id="695f7-156">Ayrıca `Boolean` , `Boolean` Aşağıdaki örnekte gösterildiği gibi, değişmez değer veya ifade kullanarak değerler atayabilirsiniz `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="695f7-156">You can also assign `Boolean` values, using either a `Boolean` literal or a `Boolean` expression, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

<span data-ttu-id="695f7-157">Benzer şekilde,,, `Char` `Date` veya veri türünün programlama öğelerine uygun değerler atayabilirsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="695f7-157">Similarly, you can assign appropriate values to programming elements of the `Char`, `Date`, or `Object` data type.</span></span> <span data-ttu-id="695f7-158">Ayrıca bir nesne örneğini, bu örneğin oluşturulduğu sınıf olarak belirtilen bir öğeye atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-158">You can also assign an object instance to an element declared to be of the class from which that instance is created.</span></span>

### <a name="compound-assignment-statements"></a><span data-ttu-id="695f7-159">Bileşik atama deyimleri</span><span class="sxs-lookup"><span data-stu-id="695f7-159">Compound assignment statements</span></span>

<span data-ttu-id="695f7-160">*Bileşik atama deyimleri* , bir programlama öğesine atamadan önce bir ifadede bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="695f7-160">*Compound assignment statements* first perform an operation on an expression before assigning it to a programming element.</span></span> <span data-ttu-id="695f7-161">Aşağıdaki örnek, `+=` işlecin sol tarafındaki değişkenin değerini sağdaki ifadenin değeri ile artıran bu işleçlerden birini gösterir.</span><span class="sxs-lookup"><span data-stu-id="695f7-161">The following example illustrates one of these operators, `+=`, which increments the value of the variable on the left side of the operator by the value of the expression on the right.</span></span>

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

<span data-ttu-id="695f7-162">Yukarıdaki örnek, değerine 1 ekler `n` ve ardından bu yeni değeri içinde depolar `n` .</span><span class="sxs-lookup"><span data-stu-id="695f7-162">The preceding example adds 1 to the value of `n`, and then stores that new value in `n`.</span></span> <span data-ttu-id="695f7-163">Bu, aşağıdaki deyimin bir toplu eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="695f7-163">It is a shorthand equivalent of the following statement:</span></span>

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

<span data-ttu-id="695f7-164">Bu türdeki işleçler kullanılarak çeşitli bileşik atama işlemleri gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-164">A variety of compound assignment operations can be performed using operators of this type.</span></span> <span data-ttu-id="695f7-165">Bu işleçlerin bir listesi ve bunlarla ilgili daha fazla bilgi için bkz. [atama işleçleri](../../language-reference/operators/assignment-operators.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-165">For a list of these operators and more information about them, see [Assignment Operators](../../language-reference/operators/assignment-operators.md).</span></span>

<span data-ttu-id="695f7-166">Birleştirme atama işleci ( `&=` ), aşağıdaki örnekte gösterildiği gibi, zaten var olan dizelerin sonuna bir dize eklemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="695f7-166">The concatenation assignment operator (`&=`) is useful for adding a string to the end of already existing strings, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a><span data-ttu-id="695f7-167">Atama deyimlerinde tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="695f7-167">Type Conversions in Assignment Statements</span></span>

<span data-ttu-id="695f7-168">Bir değişkene, özelliğe veya dizi öğesine atadığınız değer bu hedef öğeye uygun bir veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="695f7-168">The value you assign to a variable, property, or array element must be of a data type appropriate to that destination element.</span></span> <span data-ttu-id="695f7-169">Genel olarak, hedef öğesiyle aynı veri türünde bir değer oluşturmayı denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-169">In general, you should try to generate a value of the same data type as that of the destination element.</span></span> <span data-ttu-id="695f7-170">Ancak, bazı türler atama sırasında diğer türlere dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-170">However, some types can be converted to other types during assignment.</span></span>

<span data-ttu-id="695f7-171">Veri türleri arasında dönüştürme hakkında daha fazla bilgi için bkz. [tür dönüştürmeleri Visual Basic](./data-types/type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-171">For information on converting between data types, see [Type Conversions in Visual Basic](./data-types/type-conversions.md).</span></span> <span data-ttu-id="695f7-172">Kısaca Visual Basic, belirli bir türdeki bir değeri otomatik olarak widens diğer bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="695f7-172">In brief, Visual Basic automatically converts a value of a given type to any other type to which it widens.</span></span> <span data-ttu-id="695f7-173">*Genişleyen dönüştürme* , her zaman çalışma zamanında başarılı olur ve herhangi bir veri kaybetmez.</span><span class="sxs-lookup"><span data-stu-id="695f7-173">A *widening conversion* is one in that always succeeds at run time and does not lose any data.</span></span> <span data-ttu-id="695f7-174">Örneğin, Visual Basic bir `Integer` değeri `Double` uygun olduğunda öğesine dönüştürür, çünkü `Integer` widens to `Double` .</span><span class="sxs-lookup"><span data-stu-id="695f7-174">For example, Visual Basic converts an `Integer` value to `Double` when appropriate, because `Integer` widens to `Double`.</span></span> <span data-ttu-id="695f7-175">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](./data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-175">For more information, see [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="695f7-176">*Daraltma dönüştürmeleri* (genişletme olmayan), çalışma zamanında veya veri kaybından hata riski taşır.</span><span class="sxs-lookup"><span data-stu-id="695f7-176">*Narrowing conversions* (those that are not widening) carry a risk of failure at run time, or of data loss.</span></span> <span data-ttu-id="695f7-177">Bir tür dönüştürme işlevini kullanarak açıkça bir daraltma dönüştürmesi gerçekleştirebilir veya derleyiciyi ayarlayarak tüm dönüştürmeleri gerçekleştirmek üzere derleyiciye yönlendirebilirsiniz `Option Strict Off` .</span><span class="sxs-lookup"><span data-stu-id="695f7-177">You can perform a narrowing conversion explicitly by using a type conversion function, or you can direct the compiler to perform all conversions implicitly by setting `Option Strict Off`.</span></span> <span data-ttu-id="695f7-178">Daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](./data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-178">For more information, see [Implicit and Explicit Conversions](./data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="putting-multiple-statements-on-one-line"></a><span data-ttu-id="695f7-179">Birden çok deyimi tek satıra yerleştirme</span><span class="sxs-lookup"><span data-stu-id="695f7-179">Putting multiple statements on one line</span></span>

<span data-ttu-id="695f7-180">İki nokta () karakteriyle ayrılmış tek bir satırda birden çok deyimden sahip olabilirsiniz `:` .</span><span class="sxs-lookup"><span data-stu-id="695f7-180">You can have multiple statements on a single line separated by the colon (`:`) character.</span></span> <span data-ttu-id="695f7-181">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="695f7-181">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

<span data-ttu-id="695f7-182">Bazen kullanışlı olsa da, bu tür bir sözdizimi kodunuzun okunmasını ve bakımını daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="695f7-182">Though occasionally convenient, this form of syntax makes your code hard to read and maintain.</span></span> <span data-ttu-id="695f7-183">Bu nedenle, bir ifadeyi bir satıra tutmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-183">Thus, it is recommended that you keep one statement to a line.</span></span>

## <a name="continuing-a-statement-over-multiple-lines"></a><span data-ttu-id="695f7-184">Birden çok satır üzerinde bir ifadeye devam etme</span><span class="sxs-lookup"><span data-stu-id="695f7-184">Continuing a statement over multiple lines</span></span>

<span data-ttu-id="695f7-185">Bir ifade genellikle tek bir satıra sığar, ancak çok uzun olduğunda bir satır devamlılığı dizisi kullanarak sonraki satıra devam edebilir. Bu, alt çizgi karakteri () ve ardından `_` bir satır başı gelir.</span><span class="sxs-lookup"><span data-stu-id="695f7-185">A statement usually fits on one line, but when it is too long, you can continue it onto the next line using a line-continuation sequence, which consists of a space followed by an underscore character (`_`) followed by a carriage return.</span></span> <span data-ttu-id="695f7-186">Aşağıdaki örnekte, `MsgBox` çalıştırılabilir ifade iki satır üzerinde devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="695f7-186">In the following example, the `MsgBox` executable statement is continued over two lines.</span></span>

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a><span data-ttu-id="695f7-187">Örtük satır devamlılığı</span><span class="sxs-lookup"><span data-stu-id="695f7-187">Implicit line continuation</span></span>

<span data-ttu-id="695f7-188">Birçok durumda, alt çizgi karakterini () kullanmadan sonraki ardışık satırda bir ifadeye devam edebilirsiniz `_` .</span><span class="sxs-lookup"><span data-stu-id="695f7-188">In many cases, you can continue a statement on the next consecutive line without using the underscore character (`_`).</span></span> <span data-ttu-id="695f7-189">Aşağıdaki sözdizimi öğeleri, bir sonraki kod satırında ifadesiyle dolaylı olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="695f7-189">The following syntax elements implicitly continue the statement on the next line of code.</span></span>

- <span data-ttu-id="695f7-190">Virgülden sonra ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="695f7-190">After a comma (`,`).</span></span> <span data-ttu-id="695f7-191">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-191">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- <span data-ttu-id="695f7-192">Bir açık parantezden ( `(` ) sonra veya kapatma parantezinden ( `)` ) önce.</span><span class="sxs-lookup"><span data-stu-id="695f7-192">After an open parenthesis (`(`) or before a closing parenthesis (`)`).</span></span> <span data-ttu-id="695f7-193">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-193">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- <span data-ttu-id="695f7-194">Açık bir küme ayracı ( `{` ) veya bir kapanış küme ayracı () öncesi `}` .</span><span class="sxs-lookup"><span data-stu-id="695f7-194">After an open curly brace (`{`) or before a closing curly brace (`}`).</span></span> <span data-ttu-id="695f7-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-195">For example:</span></span>

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    <span data-ttu-id="695f7-196">Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md) veya [koleksiyon başlatıcıları](./collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-196">For more information, see [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or [Collection Initializers](./collection-initializers/index.md).</span></span>

- <span data-ttu-id="695f7-197">Açık bir katıştırılmış ifadeden sonra ( `<%=` ) veya BIR `%>` XML sabit değeri içindeki katıştırılmış bir ifadenin () kapatıldıktan önce.</span><span class="sxs-lookup"><span data-stu-id="695f7-197">After an open embedded expression (`<%=`) or before the close of an embedded expression (`%>`) within an XML literal.</span></span> <span data-ttu-id="695f7-198">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-198">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   <span data-ttu-id="695f7-199">Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](./xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-199">For more information, see [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).</span></span>

- <span data-ttu-id="695f7-200">Birleştirme işlecinden sonra ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="695f7-200">After the concatenation operator (`&`).</span></span> <span data-ttu-id="695f7-201">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-201">For example:</span></span>

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   <span data-ttu-id="695f7-202">Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-202">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="695f7-203">Atama işleçleri ( `=` , `&=` ,, `:=` , `+=` , `-=` `*=` , `/=` , `\=` , `^=` , `<<=` , `>>=` ,,,,) sonra.</span><span class="sxs-lookup"><span data-stu-id="695f7-203">After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).</span></span> <span data-ttu-id="695f7-204">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-204">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="695f7-205">Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-205">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="695f7-206">İkili işleçlerden (,,,,,,,,,,,,,, `+` `-` `/` `*` `Mod` `<>` `<` `>` `<=` `>=` `^` `>>` `<<` `And` `AndAlso` , `Or` `OrElse` `Like` `Xor` ,,,,,,,,,,,,,</span><span class="sxs-lookup"><span data-stu-id="695f7-206">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span></span> <span data-ttu-id="695f7-207">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-207">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   <span data-ttu-id="695f7-208">Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-208">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="695f7-209">`Is`Ve `IsNot` işleçlerinden sonra.</span><span class="sxs-lookup"><span data-stu-id="695f7-209">After the `Is` and `IsNot` operators.</span></span> <span data-ttu-id="695f7-210">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-210">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   <span data-ttu-id="695f7-211">Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-211">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="695f7-212">Bir üye niteleyicisi karakterinden ( `.` ) sonra ve üye adından önce.</span><span class="sxs-lookup"><span data-stu-id="695f7-212">After a member qualifier character (`.`) and before the member name.</span></span> <span data-ttu-id="695f7-213">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-213">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="695f7-214">Ancak, `_` `With` ifadeyi kullanırken veya bir tür için başlatma listesinde değerler sağlayan bir üye niteleyicisi karakterini takip eden bir satır devamlılık karakteri () eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="695f7-214">However, you must include a line-continuation character (`_`) following a member qualifier character when you are using the `With` statement or supplying values in the initialization list for a type.</span></span> <span data-ttu-id="695f7-215">`=` `With` Deyim veya nesne başlatma listeleri kullanırken, atama işlecinden (örneğin,) sonra çizgiyi koparın.</span><span class="sxs-lookup"><span data-stu-id="695f7-215">Consider breaking the line after the assignment operator (for example, `=`) when you are using `With` statements or object initialization lists.</span></span> <span data-ttu-id="695f7-216">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-216">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   <span data-ttu-id="695f7-217">Daha fazla bilgi için bkz [.... WITH Ifadesiyle](../../language-reference/statements/with-end-with-statement.md) veya [nesne başlatıcılarına son: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-217">For more information, see [With...End With Statement](../../language-reference/statements/with-end-with-statement.md) or [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

- <span data-ttu-id="695f7-218">Bir XML ekseni Özellik niteleyicisi ( `.` veya `.@` veya) sonra `...` .</span><span class="sxs-lookup"><span data-stu-id="695f7-218">After an XML axis property qualifier (`.` or `.@` or `...`).</span></span> <span data-ttu-id="695f7-219">Ancak, `_` anahtar sözcüğünü kullanırken bir üye niteleyicisi belirttiğinizde bir satır devamlılık karakteri () eklemeniz gerekir `With` .</span><span class="sxs-lookup"><span data-stu-id="695f7-219">However, you must include a line-continuation character (`_`) when you specify a member qualifier when you are using the `With` keyword.</span></span> <span data-ttu-id="695f7-220">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-220">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   <span data-ttu-id="695f7-221">Daha fazla bilgi için bkz. [xml eksen özellikleri](../../language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-221">For more information, see [XML Axis Properties](../../language-reference/xml-axis/index.md).</span></span>

- <span data-ttu-id="695f7-222">Bir öznitelik belirttiğinizde küçüktür işaretinden (<) veya büyüktür işaretinden ( `>` ) önce.</span><span class="sxs-lookup"><span data-stu-id="695f7-222">After a less-than sign (<) or before a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="695f7-223">Ayrıca bir özniteliği belirttiğinizde büyüktür işaretinden ( `>` ) sonra.</span><span class="sxs-lookup"><span data-stu-id="695f7-223">Also after a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="695f7-224">Ancak, `_` derleme düzeyi veya modül düzeyi öznitelikleri belirttiğinizde bir satır devamlılık karakteri () eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="695f7-224">However, you must include a line-continuation character (`_`) when you specify assembly-level or module-level attributes.</span></span> <span data-ttu-id="695f7-225">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-225">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   <span data-ttu-id="695f7-226">Daha fazla bilgi için bkz. [özniteliklere genel bakış](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-226">For more information, see [Attributes overview](../concepts/attributes/index.md).</span></span>

- <span data-ttu-id="695f7-227">Sorgu işleçlerinden önce ve sonra ( `Aggregate` , `Distinct` ,, `From` `Group By` , `Group Join` , `Join` , `Let` , `Order By` , `Select` , `Skip` , `Skip While` , `Take` ,,,,, `Take While` , `Where` `In` `Into` `On` `Ascending` `Descending` ,,,,, ve).</span><span class="sxs-lookup"><span data-stu-id="695f7-227">Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`).</span></span> <span data-ttu-id="695f7-228">Birden çok anahtar kelimeyle ( `Order By` ,, `Group Join` `Take While` ve) oluşan sorgu işleçleri anahtar kelimeleri arasında bir satırı bozamaz `Skip While` .</span><span class="sxs-lookup"><span data-stu-id="695f7-228">You cannot break a line between the keywords of query operators that are made up of multiple keywords (`Order By`, `Group Join`, `Take While`, and `Skip While`).</span></span> <span data-ttu-id="695f7-229">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-229">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   <span data-ttu-id="695f7-230">Daha fazla bilgi için bkz. [sorgular](../../language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-230">For more information, see [Queries](../../language-reference/queries/index.md).</span></span>

- <span data-ttu-id="695f7-231">`In`Deyimdeki anahtar sözcükten sonra `For Each` .</span><span class="sxs-lookup"><span data-stu-id="695f7-231">After the `In` keyword in a `For Each` statement.</span></span> <span data-ttu-id="695f7-232">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-232">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   <span data-ttu-id="695f7-233">Daha fazla bilgi için bkz [. her biri için... Sonraki Ifade](../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-233">For more information, see [For Each...Next Statement](../../language-reference/statements/for-each-next-statement.md).</span></span>

- <span data-ttu-id="695f7-234">`From`Bir koleksiyon başlatıcısındaki anahtar sözcükten sonra.</span><span class="sxs-lookup"><span data-stu-id="695f7-234">After the `From` keyword in a collection initializer.</span></span> <span data-ttu-id="695f7-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="695f7-235">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   <span data-ttu-id="695f7-236">Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="695f7-236">For more information, see [Collection Initializers](collection-initializers/index.md).</span></span>

## <a name="adding-comments"></a><span data-ttu-id="695f7-237">Açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="695f7-237">Adding comments</span></span>

<span data-ttu-id="695f7-238">Kaynak kodu her zaman kendi kendine açıklama değil, onu yazan programcıya da.</span><span class="sxs-lookup"><span data-stu-id="695f7-238">Source code is not always self-explanatory, even to the programmer who wrote it.</span></span> <span data-ttu-id="695f7-239">Bu nedenle, çoğu programcı gömülü açıklamaların serbest bir şekilde kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="695f7-239">To help document their code, therefore, most programmers make liberal use of embedded comments.</span></span> <span data-ttu-id="695f7-240">Koddaki açıklamalar, daha sonra okuma veya bunlarla çalışan herkes için bir yordamı veya belirli bir yönergeyi açıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-240">Comments in code can explain a procedure or a particular instruction to anyone reading or working with it later.</span></span> <span data-ttu-id="695f7-241">Visual Basic, derleme sırasında açıklamaları yoksayar ve derlenen kodu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="695f7-241">Visual Basic ignores comments during compilation, and they do not affect the compiled code.</span></span>

<span data-ttu-id="695f7-242">Açıklama satırları, bir kesme işareti ( `'` ) veya `REM` arkasından bir boşluk ile başlar.</span><span class="sxs-lookup"><span data-stu-id="695f7-242">Comment lines begin with an apostrophe (`'`) or `REM` followed by a space.</span></span> <span data-ttu-id="695f7-243">Bunlar, bir dize dışında, kodda herhangi bir yere eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-243">They can be added anywhere in code, except within a string.</span></span> <span data-ttu-id="695f7-244">Bir ifadeye açıklama eklemek için, bir kesme işareti ekleyin ve `REM` sonra açıklama gelir.</span><span class="sxs-lookup"><span data-stu-id="695f7-244">To append a comment to a statement, insert an apostrophe or `REM` after the statement, followed by the comment.</span></span> <span data-ttu-id="695f7-245">Açıklamalar Ayrıca kendi ayrı hattına da gidebilir.</span><span class="sxs-lookup"><span data-stu-id="695f7-245">Comments can also go on their own separate line.</span></span> <span data-ttu-id="695f7-246">Aşağıdaki örnek bu olasılıkları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="695f7-246">The following example demonstrates these possibilities.</span></span>

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a><span data-ttu-id="695f7-247">Derleme hataları denetleniyor</span><span class="sxs-lookup"><span data-stu-id="695f7-247">Checking compilation errors</span></span>

<span data-ttu-id="695f7-248">Bir kod satırı yazdığınızda, çizgi dalgalı mavi alt çizgiyle görüntülenir (bir hata iletisi de görünebilir), bildirimde bir sözdizimi hatası vardır.</span><span class="sxs-lookup"><span data-stu-id="695f7-248">If, after you type a line of code, the line is displayed with a wavy blue underline (an error message may appear as well), there is a syntax error in the statement.</span></span> <span data-ttu-id="695f7-249">Deyimle ilgili nelerin yanlış olduğunu bulmanız gerekir (görev listesine bakarak veya fare işaretçisi ile hata üzerinde gezinerek ve hata iletisini okuyarak) ve bunu düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695f7-249">You must find out what is wrong with the statement (by looking in the task list, or hovering over the error with the mouse pointer and reading the error message) and correct it.</span></span> <span data-ttu-id="695f7-250">Kodunuzda tüm sözdizimi hatalarını düzeltene kadar, programınız doğru şekilde derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="695f7-250">Until you have fixed all syntax errors in your code, your program will fail to compile correctly.</span></span>

## <a name="related-sections"></a><span data-ttu-id="695f7-251">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="695f7-251">Related sections</span></span>

|<span data-ttu-id="695f7-252">Terim</span><span class="sxs-lookup"><span data-stu-id="695f7-252">Term</span></span>|<span data-ttu-id="695f7-253">Tanım</span><span class="sxs-lookup"><span data-stu-id="695f7-253">Definition</span></span>|
|---|---|
|[<span data-ttu-id="695f7-254">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="695f7-254">Assignment Operators</span></span>](../../language-reference/operators/assignment-operators.md)|<span data-ttu-id="695f7-255">, Ve gibi atama işleçlerini kapsayan dil başvuru sayfalarına bağlantılar sağlar `=` `*=` `&=` .</span><span class="sxs-lookup"><span data-stu-id="695f7-255">Provides links to language reference pages covering assignment operators such as `=`, `*=`, and `&=`.</span></span>|
|[<span data-ttu-id="695f7-256">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="695f7-256">Operators and Expressions</span></span>](./operators-and-expressions/index.md)|<span data-ttu-id="695f7-257">Yeni değerler sağlamak için işleçlerle öğelerin nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="695f7-257">Shows how to combine elements with operators to yield new values.</span></span>|
|[<span data-ttu-id="695f7-258">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="695f7-258">How to: Break and Combine Statements in Code</span></span>](../program-structure/how-to-break-and-combine-statements-in-code.md)|<span data-ttu-id="695f7-259">Tek bir deyimin birden çok satıra nasıl kesilmesini ve birden çok deyimin aynı satıra nasıl yerleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="695f7-259">Shows how to break a single statement into multiple lines and how to place multiple statements on the same line.</span></span>|
|[<span data-ttu-id="695f7-260">Nasıl yapılır: Etiket Deyimleri</span><span class="sxs-lookup"><span data-stu-id="695f7-260">How to: Label Statements</span></span>](../program-structure/how-to-label-statements.md)|<span data-ttu-id="695f7-261">Bir kod satırının nasıl etiketleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="695f7-261">Shows how to label a line of code.</span></span>|
